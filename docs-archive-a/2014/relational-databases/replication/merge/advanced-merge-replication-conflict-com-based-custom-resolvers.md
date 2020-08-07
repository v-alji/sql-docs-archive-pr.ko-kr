---
title: COM 기반 사용자 지정 해결 프로그램 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- COM-based resolvers [SQL Server replication]
- custom resolvers [SQL Server replication]
ms.assetid: 94195797-ad7a-4962-a8e3-b259cd13aa38
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2b28795c1a7d43bcd4e8cb3f18723e05f9e76966
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733988"
---
# <a name="com-based-custom-resolvers"></a><span data-ttu-id="814b6-102">COM-Based Custom Resolvers</span><span class="sxs-lookup"><span data-stu-id="814b6-102">COM-Based Custom Resolvers</span></span>
  <span data-ttu-id="814b6-103">사용자 지정 해결 프로그램은 기본 해결 메커니즘보다 더 높은 유연성을 제공하며 복제된 데이터를 사용하여 애플리케이션에 필요한 비즈니스 논리를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="814b6-103">Custom resolvers provide more flexibility than the default resolution mechanism, and they can implement business logic required by applications using the replicated data.</span></span> <span data-ttu-id="814b6-104">COM 기반 사용자 지정 해결 프로그램은 DLL(동적 연결 라이브러리)이며 **ICustomResolver** COM 인터페이스, 해당 메서드 및 속성, 그리고 충돌 해결을 위해 특별히 디자인된 다른 지원 인터페이스 및 유형 정의를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="814b6-104">A COM-based custom resolver is a dynamic-link library (DLL) that implements the **ICustomResolver** COM interface, its methods and properties, and other supporting interfaces and type definitions designed specifically for conflict resolution.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="814b6-105">가능하면 COM 기반 사용자 지정 해결 프로그램보다 비즈니스 논리 처리기를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="814b6-105">It is recommended to use a business logic handler rather than a COM-based custom resolver if possible.</span></span> <span data-ttu-id="814b6-106">비즈니스 논리 처리기에 대한 자세한 내용은 [병합 동기화 중 비즈니스 논리 실행](execute-business-logic-during-merge-synchronization.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="814b6-106">For more information on business logic handlers, see [Execute Business Logic During Merge Synchronization](execute-business-logic-during-merge-synchronization.md).</span></span>  
  
 <span data-ttu-id="814b6-107">사용자 지정 COM 해결 프로그램을 작성하려면 replrec.dll에 제공된 형식 라이브러리를 사용합니다. 기본적으로 이 라이브러리는 [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="814b6-107">To build a custom COM resolver, you can use the type library that is provided in the replrec.dll; by default, this library is installed at [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM.</span></span>  
  
 <span data-ttu-id="814b6-108">사용자 지정 COM 해결 프로그램을 작성하기 전 다음 사항을 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="814b6-108">Before writing a custom COM resolver, you need to decide:</span></span>  
  
-   <span data-ttu-id="814b6-109">해결하려는 행 변경의 유형(예: 업데이트, 삽입 및 삭제) 및 해결 프로그램을 병합 변경 내용을 업로드하는 동안 호출할지 병합 변경 내용을 다운로드하는 동안 호출할지 또는 두 작업 모두를 수행하는 동안 호출할지 여부.</span><span class="sxs-lookup"><span data-stu-id="814b6-109">The types of row changes you want to resolve, such as updates, inserts, and deletes, and whether the resolver should be invoked during the upload of merge changes, the download of merge changes, or both.</span></span> <span data-ttu-id="814b6-110">사용자는 하나의 변경 내용, 모든 변경 내용 또는 변경 내용이 조합된 것의 유형을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="814b6-110">You can specify one type of change, all changes, or any combination.</span></span> <span data-ttu-id="814b6-111">기본 병합 충돌 해결 프로그램은 사용자 지정 해결 프로그램이 해결하지 못하는 충돌을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="814b6-111">The default merge conflict resolver handles any conflicts not covered by a custom resolver.</span></span>  
  
-   <span data-ttu-id="814b6-112">충돌 해결 시 열 추적의 사용 여부.</span><span class="sxs-lookup"><span data-stu-id="814b6-112">Whether to use column tracking when resolving the conflict.</span></span> <span data-ttu-id="814b6-113">열 추적이 설정되어 있으면 충돌이 존재하는 열의 데이터만 충돌로 플래그가 지정되며, 그렇지 않을 경우에 데이터는 병합됩니다.</span><span class="sxs-lookup"><span data-stu-id="814b6-113">When column-level tracking is on, only data in those columns where a conflict exists are flagged as a conflict, otherwise the data is merged.</span></span> <span data-ttu-id="814b6-114">그러나 충돌은 행 수준 추적에서와 같은 방법으로 해결됩니다. 즉, 우선 순위 적용 항목이 데이터 전체 행을 덮어씁니다. 그러나 데이터는 게시자나 구독자의 값 또는 게시자 및 구독자가 아닌 위치의 일부 변경된 값이 혼합된 것일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="814b6-114">However, conflicts are resolved in the same way as row-level tracking: the priority winner overwrites the entire row of data (but the data can be a mix of values from the Publisher, Subscribers, or some altered values that were from neither Publisher nor Subscribers).</span></span> <span data-ttu-id="814b6-115">자세한 내용은 [병합 복제 충돌 감지 및 해결](advanced-merge-replication-conflict-detection-and-resolution.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="814b6-115">For more information, see [Detect and Resolve Merge Replication Conflicts](advanced-merge-replication-conflict-detection-and-resolution.md).</span></span>  
  
 <span data-ttu-id="814b6-116">COM 기반 사용자 지정 충돌 해결 프로그램을 구현하려면 [병합 아티클용 사용자 지정 충돌 해결 프로그램 구현](../implement-a-custom-conflict-resolver-for-a-merge-article.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="814b6-116">To implement a COM-based custom conflict resolver, see [Implement a Custom Conflict Resolver for a Merge Article](../implement-a-custom-conflict-resolver-for-a-merge-article.md).</span></span>  
  
 <span data-ttu-id="814b6-117">사용자 지정 해결 프로그램은 전체 게시에 대해서가 아니라 아티클에 대해 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="814b6-117">A custom resolver is specified for an article, not an entire publication.</span></span> <span data-ttu-id="814b6-118">하나 이상의 아티클에 대해서 동일한 해결 프로그램을 사용할 수 있지만 사용자 지정 해결 프로그램의 논리는 특정 테이블에만 적용되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="814b6-118">The same resolver can be used with more than one article, but the logic in custom resolvers is often specific to a particular table.</span></span> <span data-ttu-id="814b6-119">해결 프로그램을 만든 후 아티클에 사용되는 테이블을 수정하면(예: 충돌 해결에 사용되는 열 이름 변경) 사용자 지정 해결 프로그램을 수정하고 다시 컴파일해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="814b6-119">If the table used in the article is modified after the resolver is created (for example, renaming the column name that is used in conflict resolution), the custom resolver might need to be modified and recompiled.</span></span>  
  
 <span data-ttu-id="814b6-120">사용자 지정 해결 프로그램을 지정하려면 [병합 아티클 해결 프로그램 지정](../publish/specify-a-merge-article-resolver.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="814b6-120">To specify a custom resolver, see [Specify a Merge Article Resolver](../publish/specify-a-merge-article-resolver.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="814b6-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="814b6-121">See Also</span></span>  
 <span data-ttu-id="814b6-122">[Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="814b6-122">[Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md) </span></span>  
 [<span data-ttu-id="814b6-123">Microsoft COM-Based Resolvers</span><span class="sxs-lookup"><span data-stu-id="814b6-123">Microsoft COM-Based Resolvers</span></span>](advanced-merge-replication-conflict-com-based-resolvers.md)  
  
  

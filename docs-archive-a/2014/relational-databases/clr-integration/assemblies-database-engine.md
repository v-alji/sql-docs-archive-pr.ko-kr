---
title: 어셈블리 (데이터베이스 엔진) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration]
- assemblies [CLR integration], about assemblies
- managed code [SQL Server], assemblies
ms.assetid: 4b146437-3061-47f6-9e8c-26eeea10b54e
author: rothja
ms.author: jroth
ms.openlocfilehash: 7edb18ccfa9954fe52093f87948f956c2eacc1b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735363"
---
# <a name="assemblies-database-engine"></a><span data-ttu-id="ea625-102">어셈블리(데이터베이스 엔진)</span><span class="sxs-lookup"><span data-stu-id="ea625-102">Assemblies (Database Engine)</span></span>
  <span data-ttu-id="ea625-103">이 섹션의 항목에서는 어셈블리를 이해하고 어셈블리를 디자인 및 구현하는 데 도움이 되는 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ea625-103">The topics in this section provide information to help you understand, design, and implement assemblies.</span></span>  
  
 <span data-ttu-id="ea625-104">어셈블리는 인스턴스에서 사용 되는 DLL 파일로 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 함수, 저장 프로시저, 트리거, 사용자 정의 집계 및 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] CLR (공용 언어 런타임)에 의해 호스팅되는 관리 코드 언어 중 하나로 작성 되는 사용자 정의 형식입니다 [!INCLUDE[tsql](../../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ea625-104">Assemblies are DLL files used in an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to deploy functions, stored procedures, triggers, user-defined aggregates, and user-defined types that are written in one of the managed code languages hosted by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] common language runtime (CLR), instead of in [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="ea625-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 어셈블리는 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 공용 언어 런타임으로 작성된 관리 애플리케이션 모듈(.dll 파일)을 참조하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="ea625-105">An assembly in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is an object that references a managed application module (.dll file) that was created in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] common language runtime.</span></span> <span data-ttu-id="ea625-106">어셈블리에는 클래스 메타데이터와 관리 코드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea625-106">An assembly contains class metadata and managed code.</span></span> <span data-ttu-id="ea625-107">어셈블리를 SQL Server 인스턴스에 업로드하는 단계는 다음과 같은 데이터베이스 개체를 만들기 위한 첫 번째 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="ea625-107">Uploading an assembly to an instance of SQL Server is the first step toward creating any of the following database objects:</span></span>  
  
-   <span data-ttu-id="ea625-108">CLR 함수.</span><span class="sxs-lookup"><span data-stu-id="ea625-108">CLR functions.</span></span> <span data-ttu-id="ea625-109">자세한 내용은 [CLR 함수 만들기](../user-defined-functions/create-clr-functions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ea625-109">For more information, see [Create CLR Functions](../user-defined-functions/create-clr-functions.md).</span></span>  
  
-   <span data-ttu-id="ea625-110">CLR 저장 프로시저.</span><span class="sxs-lookup"><span data-stu-id="ea625-110">CLR stored procedures.</span></span> <span data-ttu-id="ea625-111">자세한 내용은 [CLR 저장 프로시저](../../database-engine/dev-guide/clr-stored-procedures.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ea625-111">For more information, see [CLR Stored Procedures](../../database-engine/dev-guide/clr-stored-procedures.md).</span></span>  
  
-   <span data-ttu-id="ea625-112">CLR 트리거.</span><span class="sxs-lookup"><span data-stu-id="ea625-112">CLR triggers.</span></span> <span data-ttu-id="ea625-113">자세한 내용은 [CLR 트리거 만들기](../triggers/create-clr-triggers.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ea625-113">For more information, see [Create CLR Triggers](../triggers/create-clr-triggers.md).</span></span>  
  
-   <span data-ttu-id="ea625-114">사용자 정의 집계 함수.</span><span class="sxs-lookup"><span data-stu-id="ea625-114">User-defined aggregate functions.</span></span> <span data-ttu-id="ea625-115">자세한 내용은 [사용자 정의 집계 만들기](../user-defined-functions/create-user-defined-aggregates.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ea625-115">For more information, see [Create User-defined Aggregates](../user-defined-functions/create-user-defined-aggregates.md).</span></span>  
  
-   <span data-ttu-id="ea625-116">사용자 정의 유형.</span><span class="sxs-lookup"><span data-stu-id="ea625-116">User-defined types.</span></span> <span data-ttu-id="ea625-117">자세한 내용은 [사용자 정의 형식 사용](../native-client/features/using-user-defined-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ea625-117">For more information, see [Using User-Defined Types](../native-client/features/using-user-defined-types.md).</span></span>  
  
 <span data-ttu-id="ea625-118">어셈블리는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 다음과 같은 기능을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ea625-118">Assemblies perform the following functions in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="ea625-119">앞에 나열된 CLR 데이터베이스 개체 중 하나 이상의 기능을 수행하는 관리 코드를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ea625-119">Contain the managed code that runs the functionality of one or more of the CLR database objects previously listed.</span></span>  
  
-   <span data-ttu-id="ea625-120">버전 번호와 어셈블리 culture를 포함하는 메타데이터, 어셈블리의 클래스 목록을 고유하게 식별하는 선택적 공개 키, 어셈블리에 정의된 메서드 및 어셈블리의 프로세서 아키텍처를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ea625-120">Contain metadata that includes the version number and culture of the assembly, an optional public key that uniquely identifies the list of classes of the assembly, the methods that are defined in the assembly, and the processor architecture of the assembly.</span></span>  
  
-   <span data-ttu-id="ea625-121">관리 코드가 코드 액세스 권한을 규제하여 리소스 외부에 액세스할 수 있는 정도를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="ea625-121">Manage the degree to which managed code can access outside resources by regulating code access permissions.</span></span>  
  
-   <span data-ttu-id="ea625-122">어셈블리에 의해 참조되는 다른 어셈블리의 종속 관계에 대한 메타데이터를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ea625-122">Contain metadata about dependencies on other assemblies that are referenced by the assembly.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ea625-123">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="ea625-123">In This Section</span></span>  
  
|<span data-ttu-id="ea625-124">항목</span><span class="sxs-lookup"><span data-stu-id="ea625-124">Topic</span></span>|<span data-ttu-id="ea625-125">설명</span><span class="sxs-lookup"><span data-stu-id="ea625-125">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="ea625-126">어셈블리 디자인</span><span class="sxs-lookup"><span data-stu-id="ea625-126">Designing Assemblies</span></span>](assemblies-designing.md)|<span data-ttu-id="ea625-127">어셈블리를 만들기 전에 고려해야 하는 항목에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ea625-127">Explains what you have to consider before creating an assembly.</span></span> <span data-ttu-id="ea625-128">여기에는 어셈블리 패키지, 코드 액세스 권한 및 기타 제한 사항이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea625-128">This includes packaging assemblies, code access permissions, and other restrictions.</span></span>|  
|[<span data-ttu-id="ea625-129">어셈블리 구현</span><span class="sxs-lookup"><span data-stu-id="ea625-129">Implementing Assemblies</span></span>](assemblies-implementing.md)|<span data-ttu-id="ea625-130">어셈블리를 만들고 삭제하는 방법, 어셈블리 수정 방법 및 시기, 어셈블리에 대한 메타데이터 검색 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ea625-130">Explains how to create and drop assemblies, how and when to modify assemblies, and how to retrieve metadata about assemblies.</span></span>|  
|[<span data-ttu-id="ea625-131">어셈블리에 대한 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="ea625-131">Getting Information About Assemblies</span></span>](assemblies-getting-information.md)|<span data-ttu-id="ea625-132">어셈블리에 대한 메타데이터를 쿼리할 수 있는 카탈로그 뷰 및 함수를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="ea625-132">Lists the catalog views and functions that can be queried for metadata about assemblies.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ea625-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ea625-133">See Also</span></span>  
 [<span data-ttu-id="ea625-134">CLR&#40;공용 언어 런타임&#41; 통합 프로그래밍 개요</span><span class="sxs-lookup"><span data-stu-id="ea625-134">Common Language Runtime &#40;CLR&#41; Integration Programming Concepts</span></span>](common-language-runtime-clr-integration-programming-concepts.md)  
  
  

---
title: 구독자 유형 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.subscribertypes.f1
ms.assetid: a70656cb-21c9-4489-be77-ccd396747e3b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4d356377dec1f5307fa136c94ea682c0824479a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660502"
---
# <a name="subscriber-types"></a><span data-ttu-id="8de41-102">구독자 유형</span><span class="sxs-lookup"><span data-stu-id="8de41-102">Subscriber Types</span></span>
  <span data-ttu-id="8de41-103">병합 복제를 사용하여 게시가 지원해야 하는 구독자 유형을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8de41-103">Merge replication allows you to specify the types of Subscribers that a publication must support.</span></span> <span data-ttu-id="8de41-104">구독자 유형을 선택하면 게시에서 사용할 수 있는 기능을 결정하는 *게시 호환성 수준*이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8de41-104">Selecting Subscriber types sets the *publication compatibility level*, which determines which features can be used by a publication.</span></span>  
  
 <span data-ttu-id="8de41-105">게시 스냅샷을 만든 후 **게시 속성** 대화 상자의 **일반** 페이지에서 게시 호환성 수준을 높여 제한을 강화할 수 있습니다. 호환성 수준은 낮출 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8de41-105">After a publication snapshot is created, the publication compatibility level can be increased (made more restrictive) on the **General** page of the **Publication Properties** dialog box; the compatibility level cannot be decreased.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8de41-106">옵션</span><span class="sxs-lookup"><span data-stu-id="8de41-106">Options</span></span>  
 <span data-ttu-id="8de41-107">이 게시가 지원해야 하는 각 구독자 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8de41-107">Select each Subscriber type that this publication must support.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 <span data-ttu-id="8de41-108">게시가 모든 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8de41-108">The publication can use all features.</span></span>  
  
 [!INCLUDE[ssEW](../../includes/ssew-md.md)]  
 <span data-ttu-id="8de41-109">게시에서 사용하는 스냅샷 파일이 문자 형식이어야 합니다. 이는 스냅샷 에이전트에서 자동으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="8de41-109">The publication requires snapshot files to be in character format (this is handled automatically by the Snapshot Agent).</span></span> <span data-ttu-id="8de41-110">또한[!INCLUDE[ssEW](../../includes/ssew-md.md)] 에는 호환성 수준과 관련되지 않은 제한 사항이 많이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8de41-110">[!INCLUDE[ssEW](../../includes/ssew-md.md)] also has a number of restrictions not related to compatibility level.</span></span>  
  
 <span data-ttu-id="8de41-111">이 옵션을 선택하면 게시에 웹 동기화 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8de41-111">If this option is selected, the Web synchronization option is enabled for the publication.</span></span> <span data-ttu-id="8de41-112">웹 동기화에 대한 자세한 내용은 [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8de41-112">For more information about Web synchronization, see [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8de41-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8de41-113">See Also</span></span>  
 <span data-ttu-id="8de41-114">[데이터 및 데이터베이스 개체 게시](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="8de41-114">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="8de41-115">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="8de41-115">[Create a Publication](publish/create-a-publication.md) </span></span>  
 [<span data-ttu-id="8de41-116">배포자 및 게시자 속성 보기 및 수정</span><span class="sxs-lookup"><span data-stu-id="8de41-116">View and Modify Distributor and Publisher Properties</span></span>](view-and-modify-distributor-and-publisher-properties.md)   

  

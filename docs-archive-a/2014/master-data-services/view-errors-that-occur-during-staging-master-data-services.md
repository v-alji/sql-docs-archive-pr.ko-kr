---
title: 준비 프로세스 중에 발생 하는 오류 보기 (MDS(Master Data Services)) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- staging process [Master Data Services], viewing errors
ms.assetid: 6d2bff84-624b-47fc-a4a5-d9ea01d13412
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3b39d039b29090f3021c764126ebb782ce25cbfe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731792"
---
# <a name="view-errors-that-occur-during-the-staging-process-master-data-services"></a><span data-ttu-id="3239f-102">준비 프로세스 동안 발생하는 오류 보기(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3239f-102">View Errors that Occur During the Staging Process (Master Data Services)</span></span>
  <span data-ttu-id="3239f-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서는 준비 프로세스 동안 발생하는 오류를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3239f-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can view errors that occur during the staging process.</span></span> <span data-ttu-id="3239f-104">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스에는 오류를 표시하는 두 개의 뷰가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3239f-104">In the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database, there are two views that show errors:</span></span>  
  
-   <span data-ttu-id="3239f-105">stg.viw_name_MemberErrorDetails 뷰는 리프 또는 통합 멤버 업데이트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3239f-105">stg.viw_name_MemberErrorDetails for leaf or consolidated member updates.</span></span>  
  
-   <span data-ttu-id="3239f-106">stg.viw_name_RelationshipErrorDetails 뷰는 계층 관계 업데이트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3239f-106">stg.viw_name_RelationshipErrorDetails for hierarchy relationship updates.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3239f-107">필수 조건</span><span class="sxs-lookup"><span data-stu-id="3239f-107">Prerequisites</span></span>  
 <span data-ttu-id="3239f-108">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="3239f-108">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="3239f-109">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스에서 stg.viw_name_MemberErrorDetails 또는 stg.viw_name_RelationshipErrorDetails 뷰에 대한 SELECT 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3239f-109">In the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database, you must have SELECT permissions to either the stg.viw_name_MemberErrorDetails or stg.viw_name_RelationshipErrorDetails view.</span></span>  
  
-   <span data-ttu-id="3239f-110">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3239f-110">You must be a model administrator.</span></span> <span data-ttu-id="3239f-111">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3239f-111">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-view-staging-errors"></a><span data-ttu-id="3239f-112">준비 오류를 보려면</span><span class="sxs-lookup"><span data-stu-id="3239f-112">To view staging errors</span></span>  
  
1.  <span data-ttu-id="3239f-113">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 을 열고 [!INCLUDE[ssDE](../includes/ssde-md.md)] 데이터베이스의 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3239f-113">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] instance for your [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="3239f-114">새 쿼리를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3239f-114">Open a new query.</span></span>  
  
3.  <span data-ttu-id="3239f-115">다음 텍스트를 입력하여 준비 테이블의 이름을 예를 들어 viw_Product_MemberErrorDetails 등으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="3239f-115">Type the following text, replacing name with the name of your staging table, for example, viw_Product_MemberErrorDetails.</span></span>  
  
     `SELECT * FROM stg.viw_name_MemberErrorDetails`  
  
4.  <span data-ttu-id="3239f-116">쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3239f-116">Excecute the query.</span></span> <span data-ttu-id="3239f-117">오류 세부 정보가 **ErrorDescription** 필드에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3239f-117">Error details are displayed in the **ErrorDescription** field.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="3239f-118">다음 단계</span><span class="sxs-lookup"><span data-stu-id="3239f-118">Next Steps</span></span>  
 <span data-ttu-id="3239f-119">오류 메시지에 대한 자세한 내용은 [준비 프로세스 오류&#40;Master Data Services&#41;](../../2014/master-data-services/staging-process-errors-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3239f-119">For more details on error messages, see [Staging Process Errors &#40;Master Data Services&#41;](../../2014/master-data-services/staging-process-errors-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3239f-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3239f-120">See Also</span></span>  
 <span data-ttu-id="3239f-121">[데이터 가져오기 &#40;MDS(Master Data Services)&#41;](overview-importing-data-from-tables-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="3239f-121">[Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md) </span></span>  
 [<span data-ttu-id="3239f-122">준비 프로세스 문제 해결(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3239f-122">Troubleshooting the Staging Process (Master Data Services)</span></span>](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-the-staging-process-master-data-services.aspx)  
  
  

---
title: 버전 삭제(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- versions [Master Data Services], deleting
- deleting versions [Master Data Services]
ms.assetid: 2a4eeffe-8379-4744-ad44-c27d8c8ac9a8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f83a3bc396b2a13ac7ac03ef653b16a0d556189a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660654"
---
# <a name="delete-a-version-master-data-services"></a><span data-ttu-id="37737-102">버전 삭제(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="37737-102">Delete a Version (Master Data Services)</span></span>
  <span data-ttu-id="37737-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서는 버전에 연결된 마스터 데이터가 더 이상 필요하지 않은 경우 해당 버전을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37737-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete a version when you are sure you no longer need the master data associated with the version.</span></span> <span data-ttu-id="37737-104">버전을 삭제한 후에는 연결된 마스터 데이터를 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="37737-104">After you delete a version, you cannot retrieve the associated master data.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="37737-105">모델에 버전이 하나뿐인 경우 해당 버전을 삭제하면 모델을 사용할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37737-105">If a model has only one version and you delete it, the model becomes unusable.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="37737-106">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="37737-106">Prerequisites</span></span>  
 <span data-ttu-id="37737-107">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="37737-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="37737-108">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스에서 mdm.viw_SYSTEM_SCHEMA_VERSION 뷰를 보고 mds.udpVersionDelete 저장 프로시저를 실행할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37737-108">You must have permission to view the mdm.viw_SYSTEM_SCHEMA_VERSION view and to execute the mds.udpVersionDelete stored procedure in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="37737-109">자세한 내용은 [데이터베이스 개체 보안&#40;Master Data Services&#41;](database-object-security-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="37737-109">For more information, see [Database Object Security &#40;Master Data Services&#41;](database-object-security-master-data-services.md).</span></span>  
  
### <a name="to-delete-a-version"></a><span data-ttu-id="37737-110">버전을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="37737-110">To delete a version</span></span>  
  
1.  <span data-ttu-id="37737-111">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 을 열고 [!INCLUDE[ssDE](../includes/ssde-md.md)] 데이터베이스의 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="37737-111">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] instance for your [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="37737-112">mdm.viw_SYSTEM_SCHEMA_VERSION 뷰를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="37737-112">Open the mdm.viw_SYSTEM_SCHEMA_VERSION view.</span></span>  
  
3.  <span data-ttu-id="37737-113">삭제할 모델 버전을 찾아 **ID** 필드의 값을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="37737-113">Find the version of the model you want to delete and copy the value in the **ID** field.</span></span>  
  
4.  <span data-ttu-id="37737-114">새 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="37737-114">Create a new query.</span></span>  
  
5.  <span data-ttu-id="37737-115">다음 텍스트를 입력합니다. 여기서 *version_ID* 를 2단계에서 복사한 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="37737-115">Type the following text, replacing *version_ID* with the value you copied in step 2.</span></span>  
  
    ```  
    EXEC [mdm].[udpVersionDelete] @Version_ID='version_ID'  
    ```  
  
6.  <span data-ttu-id="37737-116">쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="37737-116">Run the query.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="37737-117">웹 애플리케이션에서 변경 내용을 반영할 때까지 몇 분간 기다려야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37737-117">You may have to wait a few minutes before the Web application reflects the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37737-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="37737-118">See Also</span></span>  
 <span data-ttu-id="37737-119">[버전 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/versions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="37737-119">[Versions &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md) </span></span>  
 [<span data-ttu-id="37737-120">버전 복사&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="37737-120">Copy a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/copy-a-version-master-data-services.md)  
  
  

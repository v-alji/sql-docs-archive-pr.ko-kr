---
title: 유효성 검사 저장 프로시저(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 332d3c86-4440-4f12-a6cb-ffbfbccde52c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8fa6b01d950c87768d10b0252c1ccbab2b932fe1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651062"
---
# <a name="validation-stored-procedure-master-data-services"></a><span data-ttu-id="669ba-102">유효성 검사 저장 프로시저(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="669ba-102">Validation Stored Procedure (Master Data Services)</span></span>
  <span data-ttu-id="669ba-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서는 버전의 유효성을 검사하여 모델 버전의 모든 멤버에 비즈니스 규칙을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="669ba-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], validate a version to apply business rules to all members in the model version.</span></span>  
  
 <span data-ttu-id="669ba-104">이 항목에서는 **mdm.udpValidateModel** 저장 프로시저를 사용하여 데이터의 유효성을 검사하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="669ba-104">This topic explains how to use the **mdm.udpValidateModel** stored procedure to validate data.</span></span> <span data-ttu-id="669ba-105">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 웹 애플리케이션에서 관리자는 UI에서 유효성 검사를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="669ba-105">If you are an administrator in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application, you can do validation in the UI instead.</span></span> <span data-ttu-id="669ba-106">자세한 내용은 [비즈니스 규칙에 대해 버전 유효성 검사&#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="669ba-106">For more information, see [Validate a Version against Business Rules &#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="669ba-107">준비 프로세스 완료 전에 유효성 검사를 호출하는 경우, 준비 프로세스가 완료되지 않은 멤버는 유효성 검사가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="669ba-107">If you invoke validation before the staging process is complete, members that have not finished staging will not be validated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="669ba-108">예제</span><span class="sxs-lookup"><span data-stu-id="669ba-108">Example</span></span>  
  
```  
DECLARE @ModelName nVarchar(50) = 'Customer'   
DECLARE @Model_id int   
DECLARE @UserName nvarchar(50)= 'DOMAIN\user_name'   
DECLARE @User_ID int   
DECLARE @Version_ID int   
  
SET @User_ID = (SELECT ID    
                 FROM mdm.tblUser u   
                 WHERE u.UserName = @UserName)   
SET @Model_ID = (SELECT Top 1 Model_ID   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_Name = @ModelName)   
SET @Version_ID = (SELECT MAX(ID)   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_ID = @Model_ID)  
  
EXECUTE mdm.udpValidateModel @User_ID, @Model_ID, @Version_ID, 1  
  
```  
  
## <a name="parameters"></a><span data-ttu-id="669ba-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="669ba-109">Parameters</span></span>  
 <span data-ttu-id="669ba-110">이 프로시저의 매개 변수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="669ba-110">The parameters of this procedure are as follows:</span></span>  
  
|<span data-ttu-id="669ba-111">매개 변수</span><span class="sxs-lookup"><span data-stu-id="669ba-111">Parameter</span></span>|<span data-ttu-id="669ba-112">Description</span><span class="sxs-lookup"><span data-stu-id="669ba-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="669ba-113">UserID</span><span class="sxs-lookup"><span data-stu-id="669ba-113">UserID</span></span>|<span data-ttu-id="669ba-114">사용자 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="669ba-114">The user ID.</span></span>|  
|<span data-ttu-id="669ba-115">Model_ID</span><span class="sxs-lookup"><span data-stu-id="669ba-115">Model_ID</span></span>|<span data-ttu-id="669ba-116">모델 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="669ba-116">The model ID.</span></span>|  
|<span data-ttu-id="669ba-117">Version_ID</span><span class="sxs-lookup"><span data-stu-id="669ba-117">Version_ID</span></span>|<span data-ttu-id="669ba-118">버전 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="669ba-118">The version ID.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="669ba-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="669ba-119">See Also</span></span>  
 <span data-ttu-id="669ba-120">[데이터 가져오기 &#40;MDS(Master Data Services)&#41;](overview-importing-data-from-tables-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="669ba-120">[Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md) </span></span>  
 [<span data-ttu-id="669ba-121">비즈니스 규칙에 대해 버전 유효성 검사&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="669ba-121">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](validate-a-version-against-business-rules-master-data-services.md)  
  
  

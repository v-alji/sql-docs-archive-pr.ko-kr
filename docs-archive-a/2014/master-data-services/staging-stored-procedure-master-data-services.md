---
title: 준비 저장 프로시저(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 6a613106-9f87-4caf-a23a-a726fc6561c5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9259352350a099db5d9b18411ad4da06dfb19819
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661212"
---
# <a name="staging-stored-procedure-master-data-services"></a><span data-ttu-id="ecb2e-102">준비 저장 프로시저(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="ecb2e-102">Staging Stored Procedure (Master Data Services)</span></span>
  <span data-ttu-id="ecb2e-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 준비 프로세스를 시작할 때는 다음 세 가지 저장 프로시저 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ecb2e-103">When initiating the staging process from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], you use one of three stored procedures.</span></span>  
  
-   <span data-ttu-id="ecb2e-104">stg.udp_name_Leaf</span><span class="sxs-lookup"><span data-stu-id="ecb2e-104">stg.udp_name_Leaf</span></span>  
  
-   <span data-ttu-id="ecb2e-105">stg.udp_name_Consolidated</span><span class="sxs-lookup"><span data-stu-id="ecb2e-105">stg.udp_name_Consolidated</span></span>  
  
-   <span data-ttu-id="ecb2e-106">stg.udp_name_Relationship</span><span class="sxs-lookup"><span data-stu-id="ecb2e-106">stg.udp_name_Relationship</span></span>  
  
 <span data-ttu-id="ecb2e-107">여기서 name은 엔터티를 만들 때 지정된 준비 테이블의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ecb2e-107">Where name is the name of the staging table that was specified when the entity was created.</span></span>  
  
## <a name="staging-process-stored-procedure-parameters"></a><span data-ttu-id="ecb2e-108">준비 프로세스 저장 프로시저 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecb2e-108">Staging Process Stored Procedure Parameters</span></span>  
 <span data-ttu-id="ecb2e-109">다음 표에서는 이러한 저장 프로시저의 매개 변수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ecb2e-109">The following table lists the parameters of these stored procedures.</span></span>  
  
|<span data-ttu-id="ecb2e-110">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecb2e-110">Parameter</span></span>|<span data-ttu-id="ecb2e-111">Description</span><span class="sxs-lookup"><span data-stu-id="ecb2e-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ecb2e-112">**VersionName**</span><span class="sxs-lookup"><span data-stu-id="ecb2e-112">**VersionName**</span></span><br /><br /> <span data-ttu-id="ecb2e-113">필수</span><span class="sxs-lookup"><span data-stu-id="ecb2e-113">Required</span></span>|<span data-ttu-id="ecb2e-114">버전의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ecb2e-114">The name of the version.</span></span> <span data-ttu-id="ecb2e-115">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터 정렬 설정에 따라 대/소문자를 구분할 수도, 그렇지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecb2e-115">This may or may not be case-sensitive, depending on your [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] collation setting.</span></span>|  
|<span data-ttu-id="ecb2e-116">**LogFlag**</span><span class="sxs-lookup"><span data-stu-id="ecb2e-116">**LogFlag**</span></span><br /><br /> <span data-ttu-id="ecb2e-117">필수</span><span class="sxs-lookup"><span data-stu-id="ecb2e-117">Required</span></span>|<span data-ttu-id="ecb2e-118">준비 프로세스 동안 트랜잭션이 기록되는지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="ecb2e-118">Determines whether transactions are logged during the staging process.</span></span> <span data-ttu-id="ecb2e-119">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ecb2e-119">Possible values are:</span></span><br /><br /> <span data-ttu-id="ecb2e-120">**0**: 트랜잭션을 기록하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ecb2e-120">**0**: Do not log transactions.</span></span><br /><span data-ttu-id="ecb2e-121">**1**: 트랜잭션을 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="ecb2e-121">**1**: Log transactions.</span></span><br /><br /> <br /><br /> <span data-ttu-id="ecb2e-122">트랜잭션에 대한 자세한 내용은 [트랜잭션&#40;Master Data Services&#41;](transactions-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ecb2e-122">For more information about transactions, see [Transactions &#40;Master Data Services&#41;](transactions-master-data-services.md).</span></span>|  
|<span data-ttu-id="ecb2e-123">**BatchTag**</span><span class="sxs-lookup"><span data-stu-id="ecb2e-123">**BatchTag**</span></span><br /><br /> <span data-ttu-id="ecb2e-124">필수, 웹 서비스에서 사용하는 경우 제외</span><span class="sxs-lookup"><span data-stu-id="ecb2e-124">Required, except by web service</span></span>|<span data-ttu-id="ecb2e-125">준비 테이블에 지정된 **BatchTag** 값입니다.</span><span class="sxs-lookup"><span data-stu-id="ecb2e-125">The **BatchTag** value as specified in the staging table.</span></span>|  
|<span data-ttu-id="ecb2e-126">**Batch_ID**</span><span class="sxs-lookup"><span data-stu-id="ecb2e-126">**Batch_ID**</span></span><br /><br /> <span data-ttu-id="ecb2e-127">웹 서비스에만 필요</span><span class="sxs-lookup"><span data-stu-id="ecb2e-127">Required by web service only</span></span>|<span data-ttu-id="ecb2e-128">준비 테이블에 지정된 **Batch_ID** 값입니다.</span><span class="sxs-lookup"><span data-stu-id="ecb2e-128">The **Batch_ID** value as specified in the staging table.</span></span>|  
  
### <a name="staging-process-stored-procedure-example"></a><span data-ttu-id="ecb2e-129">준비 프로세스 저장 프로시저 예</span><span class="sxs-lookup"><span data-stu-id="ecb2e-129">Staging Process Stored Procedure Example</span></span>  
 <span data-ttu-id="ecb2e-130">다음 예에서는 준비 저장 프로시저를 사용하여 준비 프로세스를 시작하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ecb2e-130">The following example shows how to start the staging process by using the staging stored procedure.</span></span>  
  
```  
USE [DATABASE_NAME]  
GO  
  
EXEC[stg].[udp_name_Leaf]  
      @VersionName = N'VERSION_1',  
@LogFlag = 1,  
@BatchTag = N'batch1'  
  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="ecb2e-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ecb2e-131">See Also</span></span>  
 <span data-ttu-id="ecb2e-132">[유효성 검사 저장 프로시저 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="ecb2e-132">[Validation Stored Procedure &#40;Master Data Services&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md) </span></span>  
 <span data-ttu-id="ecb2e-133">[준비 프로세스를 사용 하 여 MDS(Master Data Services)에서 멤버 로드 또는 업데이트](add-update-and-delete-data-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="ecb2e-133">[Load or Update Members in Master Data Services by Using the Staging Process](add-update-and-delete-data-master-data-services.md) </span></span>  
 [<span data-ttu-id="ecb2e-134">준비 프로세스 중에 발생 하는 오류를 보려면 MDS(Master Data Services) &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="ecb2e-134">View Errors that Occur During the Staging Process &#40;Master Data Services&#41;</span></span>](view-errors-that-occur-during-staging-master-data-services.md)  
  
  

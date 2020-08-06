---
title: 참조 데이터를 사용하도록 DQS 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.admin.config.rds.f1
- sql12.dqs.administration.rdsconfiguration.f1
- sql12.dqs.administration.configuration.createDirectRDS.f1
ms.assetid: fae745e7-57a7-4cbc-8979-56ea8e392e4e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 670e984c2afabb70dece75d94701d7a3a03c95bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728732"
---
# <a name="configure-dqs-to-use-reference-data"></a><span data-ttu-id="fec5e-102">참조 데이터를 사용하도록 DQS 구성</span><span class="sxs-lookup"><span data-stu-id="fec5e-102">Configure DQS to Use Reference Data</span></span>
  <span data-ttu-id="fec5e-103">이 항목에서는 데이터를 정리하는 데 참조 데이터를 사용하도록 DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] )를 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-103">This topic describes how to configure [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) to use reference data for cleansing your data.</span></span> <span data-ttu-id="fec5e-104">Azure Marketplace 또는 다이렉트 온라인 타사 참조 데이터 공급자의 참조 데이터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-104">You could either use reference data from Azure Marketplace or from direct online third-party reference data providers.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="fec5e-105">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="fec5e-105">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="fec5e-106">필수 조건</span><span class="sxs-lookup"><span data-stu-id="fec5e-106">Prerequisites</span></span>  
 <span data-ttu-id="fec5e-107">Marketplace의 참조 데이터를 사용하려면 유효한 Marketplace 계정 키가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-107">To use reference data from Marketplace, you must have a valid Marketplace account key.</span></span> <span data-ttu-id="fec5e-108">Marketplace 계정 키를 만드는 방법에 대 한 자세한 내용은 [계정 만들기](https://go.microsoft.com/fwlink/?LinkId=212936) ()를 참조 하세요 https://go.microsoft.com/fwlink/?LinkId=212936) .</span><span class="sxs-lookup"><span data-stu-id="fec5e-108">For detailed information about creating a Marketplace account key, see [Create Your Account](https://go.microsoft.com/fwlink/?LinkId=212936) (https://go.microsoft.com/fwlink/?LinkId=212936).</span></span> <span data-ttu-id="fec5e-109">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면의 **관리** 에서 **구성** 을 클릭한 다음 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 참조 데이터 **탭에서** DataMarket 계정 ID 만들기 **를 클릭하여** 내에서 Marketplace 계정 키를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-109">You can also create a Marketplace account key from within [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] by clicking **Configuration** under **Administration** in the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, and then clicking **Create a DataMarket Account ID** under the **Reference Data** tab.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fec5e-110">보안</span><span class="sxs-lookup"><span data-stu-id="fec5e-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fec5e-111">권한</span><span class="sxs-lookup"><span data-stu-id="fec5e-111">Permissions</span></span>  
 <span data-ttu-id="fec5e-112">DQS에서 참조 데이터 서비스 설정을 구성하려면 DQS_MAIN 데이터베이스에 대한 dqs_administrator 역할이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-112">You must have the dqs_administrator role on the DQS_MAIN database to configure reference data service settings in DQS.</span></span>  
  
##  <a name="configure-dqs-to-use-reference-data-from-marketplace"></a><a name="Marketplace"></a> <span data-ttu-id="fec5e-113">Marketplace의 참조 데이터를 사용하도록 DQS 구성</span><span class="sxs-lookup"><span data-stu-id="fec5e-113">Configure DQS to Use Reference Data from Marketplace</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="fec5e-114">[Data Quality Client 응용 프로그램을 실행](../../2014/data-quality-services/run-the-data-quality-client-application.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-114">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="fec5e-115">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면의 **관리**에서 **구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-115">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, under **Administration**, click **Configuration**.</span></span>  
  
3.  <span data-ttu-id="fec5e-116">사용자 또는 사용자 조직에서 프록시 서버를 사용하여 인터넷에 연결하는 경우 **참조 데이터** 탭의 **네트워크 설정** 영역에서 **프록시 서버** 및 **포트** 상자에 적절한 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-116">In the **Reference Data** tab, under the **Network Settings** area, type appropriate values in the **Proxy Server** and **Port** boxes if you or your organization uses proxy server to connect to the Internet.</span></span>  
  
4.  <span data-ttu-id="fec5e-117">**DataMarket 계정 ID** 상자에서 Marketplace 계정 키를 지정한 다음 **DataMarket 계정 ID 확인** 아이콘을 클릭하여 계정 키의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-117">Specify the Marketplace account key in the **DataMarket Account ID** box, and click the **Validate DataMarket Account ID** icon to validate the account key.</span></span> <span data-ttu-id="fec5e-118">지정한 Marketplace 계정 키가 유효한지 여부를 나타내는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-118">A message appears to display whether the specified Marketplace account key is valid.</span></span>  
  
 <span data-ttu-id="fec5e-119">이제 DQS에서 지정한 Marketplace 계정 키로 구독하는 Marketplace의 참조 데이터 서비스를 사용할 준비가 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-119">You are now ready to use the reference data services from Marketplace in DQS that are subscribed for the specified Marketplace account key.</span></span>  
  
##  <a name="configure-dqs-to-use-reference-data-from-direct-online-third-party-reference-data-providers"></a><a name="ThirdParty"></a> <span data-ttu-id="fec5e-120">다이렉트 온라인 타사 참조 데이터 공급자의 참조 데이터를 사용하도록 DQS 구성</span><span class="sxs-lookup"><span data-stu-id="fec5e-120">Configure DQS to Use Reference Data from Direct Online Third-Party Reference Data Providers</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="fec5e-121">[Data Quality Client 응용 프로그램을 실행](../../2014/data-quality-services/run-the-data-quality-client-application.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-121">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="fec5e-122">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면의 **관리**에서 **구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-122">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, under **Administration**, click **Configuration**.</span></span>  
  
3.  <span data-ttu-id="fec5e-123">사용자 또는 사용자 조직에서 프록시 서버를 사용하여 인터넷에 연결하는 경우 **참조 데이터** 탭의 **네트워크 설정** 영역에서 **프록시 서버** 및 **포트** 상자에 적절한 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-123">In the **Reference Data** tab, under the **Network Settings** area, type appropriate values in the **Proxy Server** and **Port** boxes if you or your organization uses proxy server to connect to the Internet.</span></span>  
  
4.  <span data-ttu-id="fec5e-124">**다이렉트 온라인 타사 참조 데이터 서비스 설정** 영역에서 **새 참조 데이터 서비스 공급자 추가** 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-124">In the **Direct Online 3rd Party Reference Data Service Settings** area, click the **Add new reference data service provider** icon.</span></span>  
  
5.  <span data-ttu-id="fec5e-125">**새 다이렉트 온라인 타사 참조 데이터 서비스 공급자 만들기** 대화 상자에서 다음 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-125">In the **Create New Direct Online 3rd Party Reference Data Service Provider** dialog box, specify the following details:</span></span>  
  
    1.  <span data-ttu-id="fec5e-126">**이름** 상자에 새 다이렉트 참조 데이터 서비스 공급자의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-126">In the **Name** box, type a name of the new direct reference data service provider.</span></span>  
  
    2.  <span data-ttu-id="fec5e-127">(선택 사항) **설명** 상자에 새 다이렉트 참조 데이터 서비스 공급자에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-127">(Optional) In the **Description** box, type a description of the new direct reference data service provider.</span></span>  
  
    3.  <span data-ttu-id="fec5e-128">**범주** 상자에 새 다이렉트 참조 데이터 서비스 공급자가 제공한 데이터의 범주를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-128">In the **Category** box, type the category of the data provided by the new direct reference data service provider.</span></span>  
  
    4.  <span data-ttu-id="fec5e-129">스키마 상자에 다이렉트 참조 데이터 서비스 공급자에서 사용할 필드 문자열(열 이름)을 정의하는 스키마를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-129">In the Schema box, specify the schema that defines the string of fields (column names) to be used from the direct reference data service provider.</span></span> <span data-ttu-id="fec5e-130">필드 이름은 공백을 포함할 수 없으며, 필드는 쉼표로 구분되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-130">A field name should not contain a space, and the fields should be separated by commas.</span></span> <span data-ttu-id="fec5e-131">예를 들면 `FirstName, LastName, City, State`와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-131">For example: `FirstName, LastName, City, State`.</span></span>  
  
    5.  <span data-ttu-id="fec5e-132">**URI** 상자에 새 다이렉트 참조 데이터 서비스 공급자의 URI를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-132">In the **URI** box, type the URI of the direct reference data service provider.</span></span> <span data-ttu-id="fec5e-133">보안 URI("https://"로 시작하는 주소)만 DQS에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-133">Only secure URIs (address starting with "https://") are allowed in DQS.</span></span>  
  
    6.  <span data-ttu-id="fec5e-134">**최대 일괄 처리 크기** 상자에 정리를 위해 참조 데이터 서비스 공급자로 보낼 일괄 처리당 최대 레코드 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-134">In the **Max Batch Size** box, type the maximum number of records per batch that will be sent to the reference data service provider for cleansing.</span></span> <span data-ttu-id="fec5e-135">일괄 처리당 최대 100개의 레코드를 정리 작업에 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-135">A maximum of 100 records per batch can be specified for the cleansing activity.</span></span>  
  
    7.  <span data-ttu-id="fec5e-136">**계정 ID** 상자에 참조 데이터 서비스 공급자의 구독자 계정 ID를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-136">In the **Account ID** box, type the account ID of the subscriber with the reference data service provider.</span></span>  
  
6.  <span data-ttu-id="fec5e-137">**확인** 을 클릭하여 데이터를 저장하고 **새 다이렉트 온라인 타사 참조 데이터 서비스 공급자 만들기** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-137">Click **OK** to save the data, and close the **Create New Direct Online 3rd Party Reference Data Service Provider** dialog box.</span></span> <span data-ttu-id="fec5e-138">새로 추가한 다이렉트 온라인 타사 참조 데이터 공급자를 DQS의 **직접 참조 데이터 서비스 공급자 표** 에서 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-138">The newly added direct online third party reference data provider becomes available in the **Direct Reference Data Service Providers Grid** in DQS.</span></span>  
  
 <span data-ttu-id="fec5e-139">이제 DQS에서 새로 구성한 다이렉트 온라인 타사 참조 데이터 서비스 공급자의 참조 데이터 서비스를 사용할 준비가 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-139">You are now ready to use the reference data services from the newly configured direct online third-party reference data service provider in DQS.</span></span>  
  
##  <a name="follow-up-after-configuring-dqs-to-use-reference-data"></a><a name="FollowUp"></a><span data-ttu-id="fec5e-140">후속 작업: 참조 데이터를 사용 하도록 DQS를 구성한 후</span><span class="sxs-lookup"><span data-stu-id="fec5e-140">Follow Up: After Configuring DQS to use Reference Data</span></span>  
 <span data-ttu-id="fec5e-141">이제 방금 구성한 데이터 공급자에서 사용할 수 있는 참조 데이터에 필요한 기술 자료 도메인을 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fec5e-141">You must now map the required knowledge base domains to the reference data available from the data providers you just configured.</span></span> <span data-ttu-id="fec5e-142">이렇게 하려면 [참조 데이터에 도메인 또는 복합 도메인 연결](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fec5e-142">To do so, see [Attach a Domain or Composite Domain to Reference Data](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md).</span></span>  
  
  

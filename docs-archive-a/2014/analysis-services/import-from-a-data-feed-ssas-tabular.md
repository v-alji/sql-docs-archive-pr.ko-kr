---
title: 데이터 피드에서 가져오기 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0686e519-67c2-4f9b-8cd2-84a4871499ee
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7e5446effdcd01a3fe0eeb5dd14a1a61e97c417b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660742"
---
# <a name="import-from-a-data-feed-ssas-tabular"></a><span data-ttu-id="5a731-102">데이터 피드에서 가져오기(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="5a731-102">Import from a Data Feed (SSAS Tabular)</span></span>
  <span data-ttu-id="5a731-103">데이터 피드는 온라인 데이터 원본에서 생성되어 대상 문서 또는 애플리케이션으로 스트리밍되는 하나 이상의 XML 데이터 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-103">Data feeds are one or more XML data streams that are generated from an online data source and streamed to a destination document or application.</span></span> <span data-ttu-id="5a731-104">테이블 가져오기 마법사를 사용하여 데이터 피드의 데이터를 모델로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-104">You can import data from a data feed into your model by using the Table Import Wizard.</span></span>  
  
 <span data-ttu-id="5a731-105">이 항목에는 다음과 같은 섹션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-105">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="5a731-106">데이터 피드에서 가져오기 이해</span><span class="sxs-lookup"><span data-stu-id="5a731-106">Understanding import from a data feed</span></span>](#prereq)  
  
-   [<span data-ttu-id="5a731-107">Azure DataMarket 데이터 세트에서 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="5a731-107">Import data from an Azure DataMarket dataset</span></span>](#azure)  
  
-   [<span data-ttu-id="5a731-108">공용 또는 회사 데이터 원본에서 데이터 피드 가져오기</span><span class="sxs-lookup"><span data-stu-id="5a731-108">Import data feeds from public or corporate data sources</span></span>](#importdata)  
  
-   [<span data-ttu-id="5a731-109">SharePoint 목록에서 데이터 피드 가져오기</span><span class="sxs-lookup"><span data-stu-id="5a731-109">Import data feeds from SharePoint lists</span></span>](#importlist)  
  
-   [<span data-ttu-id="5a731-110">Reporting Services 보고서에서 데이터 피드 가져오기</span><span class="sxs-lookup"><span data-stu-id="5a731-110">Import data feeds from Reporting Services Reports</span></span>](#importreport)  
  
##  <a name="understanding-import-from-a-data-feed"></a><a name="prereq"></a><span data-ttu-id="5a731-111">데이터 피드에서 가져오기 이해</span><span class="sxs-lookup"><span data-stu-id="5a731-111">Understanding import from a data feed</span></span>  
 <span data-ttu-id="5a731-112">다음 유형의 데이터 피드에서 테이블 형식 모델로 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-112">You can import data into a Tabular Model from the following types of data feeds:</span></span>  
  
 <span data-ttu-id="5a731-113">**Reporting Services 보고서**</span><span class="sxs-lookup"><span data-stu-id="5a731-113">**Reporting Services Report**</span></span>  
 <span data-ttu-id="5a731-114">SharePoint 사이트나 보고서 서버에 게시한 Reporting Services 보고서를 모델에서 데이터 원본으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-114">You can use a Reporting Services report that has been published to a SharePoint site or a report server as a data source in a model.</span></span> <span data-ttu-id="5a731-115">Reporting Services 보고서에서 데이터를 가져올 경우 보고서 정의(.rdl) 파일을 데이터 원본으로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-115">When importing data from a Reporting Services Report, you must specify a report definition (.rdl) file as a data source.</span></span>  
  
 <span data-ttu-id="5a731-116">**Azure DataMarket 데이터 세트**</span><span class="sxs-lookup"><span data-stu-id="5a731-116">**Azure DataMarket Dataset**</span></span>  
 <span data-ttu-id="5a731-117">Azure DataMarket은 단일 마켓플레이스와 정보 배달 채널을 클라우드 서비스로 제공하는 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-117">Azure DataMarket is a service that provides a single marketplace and delivery channel for information as cloud services.</span></span> <span data-ttu-id="5a731-118">Azure DataMarket 데이터 세트에는 Windows 사용자 계정 대신 계정 키가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-118">Azure DataMarket datasets require an account key instead of a Windows user account.</span></span>  
  
 <span data-ttu-id="5a731-119">**Atom 피드**</span><span class="sxs-lookup"><span data-stu-id="5a731-119">**Atom feeds**</span></span>  
 <span data-ttu-id="5a731-120">피드는 ATOM 피드여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-120">The feed must be an Atom feed.</span></span> <span data-ttu-id="5a731-121">RSS 피드는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-121">RSS feeds are not supported.</span></span> <span data-ttu-id="5a731-122">누구나 사용할 수 있도록 피드가 공개되어 있거나 피드 연결에 필요한 권한이 현재 로그인에 사용한 Windows 계정에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-122">The feed must either be publicly available or you must have permission to connect to it under the Windows account with which you are currently logged in.</span></span>  
  
 <span data-ttu-id="5a731-123">가져오는 동안 데이터 피드의 데이터가 모델에 한 번 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-123">Data from a data feed is added into a model once during import.</span></span> <span data-ttu-id="5a731-124">피드에서 업데이트된 데이터를 가져오려면 모델 디자이너에서 데이터를 새로 고치거나, 모델이 Analysis Services의 프로덕션 인스턴스에 배포된 후 이 모델에 대해 데이터 새로 고침 일정을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-124">To get updated data from the feed, you can either refresh the data from the model designer, or configure a data refresh schedule for the model after it is deployed to a production instance of Analysis Services.</span></span> <span data-ttu-id="5a731-125">자세한 내용은 [데이터 처리&#40;SSAS 테이블 형식&#41;](process-data-ssas-tabular.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5a731-125">For more information, see [Process Data &#40;SSAS Tabular&#41;](process-data-ssas-tabular.md).</span></span>  
  
##  <a name="import-data-from-an-azure-datamarket-dataset"></a><a name="azure"></a><span data-ttu-id="5a731-126">Azure DataMarket 데이터 집합에서 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="5a731-126">Import data from an Azure DataMarket dataset</span></span>  
 <span data-ttu-id="5a731-127">Azure DataMarket의 데이터를 모델에 테이블로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-127">You can import data from an Azure DataMarket as a table in your model.</span></span>  
  
#### <a name="to-import-data-from-an-azure-datamarket-dataset"></a><span data-ttu-id="5a731-128">Azure DataMarket 데이터 세트에서 데이터를 가져오려면</span><span class="sxs-lookup"><span data-stu-id="5a731-128">To import data from an Azure DataMarket dataset</span></span>  
  
1.  <span data-ttu-id="5a731-129">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 **모델** 메뉴를 클릭한 다음 **데이터 원본에서 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-129">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Import from Data Source**.</span></span> <span data-ttu-id="5a731-130">테이블 가져오기 마법사가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-130">The Table Import Wizard opens.</span></span>  
  
2.  <span data-ttu-id="5a731-131">**데이터 원본에 연결** 페이지의 **데이터 피드**에서 **Azure DataMarket 데이터 세트**를 선택한 후, **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-131">On the **Connect to a Data Source** page, under **Data Feeds**, select **Azure DataMarket Dataset**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="5a731-132">**Azure DataMarket 데이터 세트에 연결** 페이지의 **이름**에 액세스하는 피드를 설명하는 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-132">On the **Connect to an Azure DataMarket dataset** page, in **Friendly Name**, type a descriptive name for the feed you are accessing.</span></span> <span data-ttu-id="5a731-133">피드 또는 데이터 원본을 여러 개 가져오는 경우 연결을 설명하는 이름을 사용하면 연결이 사용되는 방식을 기억하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-133">If you are importing multiple feeds or data sources, using descriptive names for the connection can help you remember how the connection is used.</span></span>  
  
4.  <span data-ttu-id="5a731-134">**데이터 피드 URL**에 데이터 피드의 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-134">In **Data Feed URL**, type the address for the data feed.</span></span>  
  
5.  <span data-ttu-id="5a731-135">**보안 설정**의 **계정 키**에 계정 키를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-135">In **Security Settings**, in **Account Key**, type an account key.</span></span> <span data-ttu-id="5a731-136">계정 키는 Analysis Services가 DataMarket 구독에 액세스할 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-136">Account keys are used by Analysis Services to access the DataMarket subscriptions.</span></span>  
  
6.  <span data-ttu-id="5a731-137">**연결 테스트** 를 클릭하여 피드를 사용할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-137">Click **Test Connection** to make sure the feed is available.</span></span> <span data-ttu-id="5a731-138">또는 **고급** 을 클릭하여 기본 URL이나 서비스 문서 URL에 피드를 제공하는 쿼리 또는 서비스 문서가 포함되어 있는지 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-138">Alternatively, you can also click **Advanced** to confirm that the Base URL or Service Document URL contains the query or service document that provides the feed.</span></span>  
  
7.  <span data-ttu-id="5a731-139">**다음** 을 클릭하여 가져오기 작업을 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-139">Click **Next** to continue with the import.</span></span>  
  
8.  <span data-ttu-id="5a731-140">**가장 정보** 페이지에서 데이터를 새로 고칠 때 Analysis Services가 데이터 원본에 연결하는 데 사용할 자격 증명을 지정하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-140">On the **Impersonation Information** page, specify the credentials that Analysis Services will use to connect to the data source when refreshing the data, and then click **Next**.</span></span> <span data-ttu-id="5a731-141">이러한 자격 증명은 계정 키와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-141">These credentials are different from the Account Key.</span></span>  
  
9. <span data-ttu-id="5a731-142">마법사의 **테이블 및 뷰 선택** 페이지에 있는 **이름** 필드에 가져온 데이터가 포함될 테이블을 설명하는 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-142">In the **Select Tables and Views** page of the wizard, in the **Friendly Name** field, type a descriptive name that identifies the table that will contain this data after it is imported</span></span>  
  
10. <span data-ttu-id="5a731-143">**미리 보기 및 필터** 를 클릭하여 데이터를 검토하고 열 선택을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-143">Click **Preview and Filter** to review the data and change column selections.</span></span> <span data-ttu-id="5a731-144">보고서 데이터 피드로 가져오는 행을 제한할 수는 없지만 해당 확인란의 선택을 취소하여 열을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-144">You cannot restrict the rows that are imported in the report data feed, but you can remove columns by clearing the check boxes.</span></span> <span data-ttu-id="5a731-145">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-145">Click **OK**.</span></span>  
  
11. <span data-ttu-id="5a731-146">**테이블 및 뷰 선택** 페이지에서 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-146">In the **Select Tables and Views** page, click **Finish**.</span></span>  
  
##  <a name="import-data-feeds-from-public-or-corporate-data-sources"></a><a name="importdata"></a><span data-ttu-id="5a731-147">공용 또는 회사 데이터 원본에서 데이터 피드 가져오기</span><span class="sxs-lookup"><span data-stu-id="5a731-147">Import data feeds from public or corporate data sources</span></span>  
 <span data-ttu-id="5a731-148">공용 피드에 액세스하거나, 소유 또는 레거시 데이터베이스 시스템에서 ATOM 피드를 생성하는 사용자 지정 데이터 서비스를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-148">You can access public feeds or build custom data services that generate Atom feeds from proprietary or legacy database systems.</span></span>  
  
#### <a name="to-import-data-from-public-or-corporate-data-feeds"></a><span data-ttu-id="5a731-149">공용 또는 회사 데이터 피드에서 데이터를 가져오려면</span><span class="sxs-lookup"><span data-stu-id="5a731-149">To import data from public or corporate data feeds</span></span>  
  
1.  <span data-ttu-id="5a731-150">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 **모델** 메뉴를 클릭한 다음 **데이터 원본에서 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-150">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Import from Data Source**.</span></span> <span data-ttu-id="5a731-151">테이블 가져오기 마법사가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-151">The Table Import Wizard opens.</span></span>  
  
2.  <span data-ttu-id="5a731-152">**데이터 원본에 연결** 페이지의 **데이터 피드**에서 **다른 피드**를 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-152">On the **Connect to a Data Source** page, under **Data Feeds**, select **Other Feeds**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="5a731-153">**데이터 피드에 연결** 페이지에서 액세스하는 피드를 설명하는 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-153">On the **Connect to a Data Feed** page, type a descriptive name for the feed you are accessing.</span></span> <span data-ttu-id="5a731-154">피드 또는 데이터 원본을 여러 개 가져오는 경우 연결을 설명하는 이름을 사용하면 연결이 사용되는 방식을 기억하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-154">If you are importing multiple feeds or data sources, using descriptive names for the connection can help you remember how the connection is used.</span></span>  
  
4.  <span data-ttu-id="5a731-155">**데이터 피드 URL**에 데이터 피드의 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-155">In **Data Feed URL**, type the address for the data feed.</span></span> <span data-ttu-id="5a731-156">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-156">Valid values include the following:</span></span>  
  
    1.  <span data-ttu-id="5a731-157">ATOM 데이터가 포함된 XML 문서.</span><span class="sxs-lookup"><span data-stu-id="5a731-157">An XML document that contains the Atom data.</span></span> <span data-ttu-id="5a731-158">예를 들어 다음 URL은 Open Government Data Initiative 웹 사이트의 공용 피드를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-158">For example, the following URL points to a public feed on the Open Government Data Initiative web site:</span></span>  
  
        ```  
        http://ogdi.cloudapp.net/v1/dc/banklocations/  
        ```  
  
    2.  <span data-ttu-id="5a731-159">하나 이상의 피드를 지정하는 .atomsvc 문서.</span><span class="sxs-lookup"><span data-stu-id="5a731-159">An .atomsvc document that specifies one or more feeds.</span></span> <span data-ttu-id="5a731-160">.atomsvc 문서는 하나 이상의 피드를 제공하는 서비스 또는 애플리케이션을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-160">An .atomsvc document points to a service or application that provides one or more feeds.</span></span> <span data-ttu-id="5a731-161">각 피드는 결과 집합을 반환하는 기본 쿼리로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-161">Each feed is specified as a base query that returns the result set.</span></span>  
  
         <span data-ttu-id="5a731-162">웹 서버에 있는 .atomsvc 문서의 URL 주소를 지정하거나 컴퓨터의 공유 또는 로컬 폴더에서 파일을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-162">You can specify a URL address to an .atomsvc document that is on a web server or you can open the file from a shared or local folder on your computer.</span></span> <span data-ttu-id="5a731-163">Reporting Services 보고서를 내보내는 동안 컴퓨터에 .atomsvc 문서를 저장한 경우 해당 문서가 있거나, 다른 사용자가 SharePoint 사이트에 대해 만든 .atomsvc 문서가 데이터 피드 라이브러리에 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-163">You might have an .atomsvc document if you saved one to your computer while exporting a Reporting Services report, or you might have .atomsvc documents in a data feed library that someone created for your SharePoint site.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="5a731-164">URL 주소나 공유 폴더를 통해 액세스할 수 있는 .atomsvc 문서를 지정하는 것이 좋습니다. 그러면 통합 문서가 SharePoint에 게시된 후 나중에 통합 문서에 대해 데이터 자동 새로 고침을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-164">Specifying an .atomsvc document that can be accessed through a URL address or shared folder is recommended because it gives you the option of configuring automatic data refresh for the workbook later, after the workbook is published to SharePoint.</span></span> <span data-ttu-id="5a731-165">컴퓨터의 로컬 위치가 아닌 위치를 지정하면 서버에서 동일한 URL 주소나 네트워크 폴더를 다시 사용하여 데이터를 새로 고칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-165">The server can re-use the same URL address or network folder to refresh data if you specify a location that is not local to your computer.</span></span>  
  
5.  <span data-ttu-id="5a731-166">**연결 테스트** 를 클릭하여 피드를 사용할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-166">Click **Test Connection** to make sure the feed is available.</span></span> <span data-ttu-id="5a731-167">또는 **고급** 을 클릭하여 기본 URL이나 서비스 문서 URL에 피드를 제공하는 쿼리 또는 서비스 문서가 포함되어 있는지 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-167">Alternatively, you can also click **Advanced** to confirm that the Base URL or Service Document URL contains the query or service document that provides the feed.</span></span>  
  
6.  <span data-ttu-id="5a731-168">**다음** 을 클릭하여 가져오기 작업을 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-168">Click **Next** to continue with the import.</span></span>  
  
7.  <span data-ttu-id="5a731-169">**가장 정보** 페이지에서 데이터를 새로 고칠 때 Analysis Services가 데이터 원본에 연결하는 데 사용할 자격 증명을 지정하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-169">On the **Impersonation Information** page, specify the credentials that Analysis Services will use to connect to the data source when refreshing the data, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="5a731-170">마법사의 **테이블 및 뷰 선택** 페이지에 있는 **이름** 필드에서 데이터 피드 내용을 가져온 데이터가 포함될 테이블을 설명하는 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-170">In the **Select Tables and Views** page of the wizard, in the **Friendly Name** field, replace Data Feed Content with a descriptive name that identifies the table that will contain this data after it is imported</span></span>  
  
9. <span data-ttu-id="5a731-171">**미리 보기 및 필터** 를 클릭하여 데이터를 검토하고 열 선택을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-171">Click **Preview and Filter** to review the data and change column selections.</span></span> <span data-ttu-id="5a731-172">보고서 데이터 피드로 가져오는 행을 제한할 수는 없지만 해당 확인란의 선택을 취소하여 열을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-172">You cannot restrict the rows that are imported in the report data feed, but you can remove columns by clearing the check boxes.</span></span> <span data-ttu-id="5a731-173">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-173">Click **OK**.</span></span>  
  
10. <span data-ttu-id="5a731-174">**테이블 및 뷰 선택** 페이지에서 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-174">In the **Select Tables and Views** page, click **Finish**.</span></span>  
  
##  <a name="import-data-feeds-from-sharepoint-lists"></a><a name="importlist"></a><span data-ttu-id="5a731-175">SharePoint 목록에서 데이터 피드 가져오기</span><span class="sxs-lookup"><span data-stu-id="5a731-175">Import data feeds from SharePoint lists</span></span>  
 <span data-ttu-id="5a731-176">(SharePoint) 리본에 **데이터 피드로 내보내기** 단추가 있는 모든 SharePoint 목록을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-176">You can import any SharePoint list that has an **Export as Data Feed** button on the (SharePoint) ribbon.</span></span> <span data-ttu-id="5a731-177">이 단추를 클릭하여 목록을 피드로 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-177">You can click this button to export the list as a feed.</span></span>  
  
#### <a name="to-import-data-feeds-from-a-sharepoint-list"></a><span data-ttu-id="5a731-178">SharePoint 목록에서 데이터 피드를 가져오려면</span><span class="sxs-lookup"><span data-stu-id="5a731-178">To import data feeds from a SharePoint list</span></span>  
  
1.  <span data-ttu-id="5a731-179">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 **모델** 메뉴를 클릭한 다음 **데이터 원본에서 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-179">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Import from Data Source**.</span></span>  
  
2.  <span data-ttu-id="5a731-180">**데이터 원본에 연결** 페이지의 **데이터 피드**에서 **다른 데이터 피드**를 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-180">On the **Connect to a Data Source** page, under **Data Feeds**, select **Other Data Feeds**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="5a731-181">**데이터 피드에 연결** 페이지에서 액세스하는 피드를 설명하는 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-181">On the **Connect to a Data Feed** page, type a descriptive name for the feed you are accessing.</span></span> <span data-ttu-id="5a731-182">피드 또는 데이터 원본을 여러 개 가져오는 경우 연결을 설명하는 이름을 사용하면 연결이 사용되는 방식을 기억하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-182">If you are importing multiple feeds or data sources, using descriptive names for the connection might help you remember how the connection is used.</span></span>  
  
4.  <span data-ttu-id="5a731-183">데이터 피드 URL에 목록 데이터 서비스의 주소를 \<server-name> SharePoint 서버의 실제 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-183">In Data Feed URL, type an address to the list data service, replacing \<server-name> with the actual name of your SharePoint server:</span></span>  
  
    ```  
    http://<server-name>/_vti_bin/listdata.svc  
    ```  
  
5.  <span data-ttu-id="5a731-184">**연결 테스트** 를 클릭하여 피드를 사용할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-184">Click **Test Connection** to make sure the feed is available.</span></span> <span data-ttu-id="5a731-185">또는 **고급** 을 클릭하여 서비스 문서 URL에 목록 데이터 서비스의 주소가 포함되어 있는지 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-185">Alternatively, you can also click **Advanced** to confirm that the Service Document URL contains an address to the list data service.</span></span>  
  
6.  <span data-ttu-id="5a731-186">**다음** 을 클릭하여 가져오기 작업을 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-186">Click **Next** to continue with the import.</span></span>  
  
7.  <span data-ttu-id="5a731-187">**가장 정보** 페이지에서 데이터를 새로 고칠 때 Analysis Services가 데이터 원본에 연결하는 데 사용할 자격 증명을 지정하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-187">On the **Impersonation Information** page, specify the credentials that Analysis Services will use to connect to the data source when refreshing the data, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="5a731-188">마법사의 **테이블 및 뷰 선택** 페이지에서 가져올 목록을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-188">In the **Select Tables and Views** page of the wizard, select the lists you want to import.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5a731-189">열이 포함된 목록만 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-189">You can only import lists that contain columns.</span></span>  
  
9. <span data-ttu-id="5a731-190">**미리 보기 및 필터** 를 클릭하여 데이터를 검토하고 열 선택을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-190">Click **Preview and Filter** to review the data and change column selections.</span></span> <span data-ttu-id="5a731-191">보고서 데이터 피드로 가져오는 행을 제한할 수는 없지만 해당 확인란의 선택을 취소하여 열을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-191">You cannot restrict the rows that are imported in the report data feed, but you can remove columns by clearing the check boxes.</span></span> <span data-ttu-id="5a731-192">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-192">Click **OK**.</span></span>  
  
10. <span data-ttu-id="5a731-193">**테이블 및 뷰 선택** 페이지에서 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-193">In the **Select Tables and Views** page, click **Finish**.</span></span>  
  
##  <a name="import-data-feeds-from-reporting-services-reports"></a><a name="importreport"></a><span data-ttu-id="5a731-194">Reporting Services 보고서에서 데이터 피드 가져오기</span><span class="sxs-lookup"><span data-stu-id="5a731-194">Import data feeds from Reporting Services Reports</span></span>  
 <span data-ttu-id="5a731-195">[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] Reporting Services가 배포되어 있는 경우 Atom 렌더링 확장 프로그램을 사용하여 기존 보고서에서 데이터 피드를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-195">If you have a deployment of [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] Reporting Services, you can use the Atom rendering extension to generate a data feed from an existing report.</span></span>  
  
#### <a name="to-import-report-data-from-a-published-reporting-services-report"></a><span data-ttu-id="5a731-196">게시된 Reporting Services 보고서에서 보고서 데이터를 가져오려면</span><span class="sxs-lookup"><span data-stu-id="5a731-196">To import report data from a published Reporting Services report</span></span>  
  
1.  <span data-ttu-id="5a731-197">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 **모델** 메뉴를 클릭한 다음 **데이터 원본에서 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-197">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Import from Data Source**.</span></span>  
  
2.  <span data-ttu-id="5a731-198">**데이터 원본에 연결** 페이지의 **데이터 피드**에서 **보고서**를 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-198">On the **Connect to a Data Source** page, under **Data Feeds**, select **Report**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="5a731-199">Microsoft SQL Server Reporting Services 보고서에 연결 페이지의 연결 이름에 액세스하는 피드를 설명하는 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-199">On the Connect to a Microsoft SQL Server Reporting Services Report page, in Friendly Connection Name, type a descriptive name for the feed you are accessing.</span></span> <span data-ttu-id="5a731-200">데이터 원본을 여러 개 가져오는 경우 연결을 설명하는 이름을 사용하면 연결이 사용되는 방식을 기억하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-200">If you are importing multiple data sources, using descriptive names for the connection might help you remember how the connection is used.</span></span>  
  
4.  <span data-ttu-id="5a731-201">**찾아보기** 를 클릭하고 보고서 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-201">Click **Browse** and select a report server.</span></span>  
  
     <span data-ttu-id="5a731-202">보고서 서버에서 보고서를 정기적으로 사용하는 경우 해당 서버가 **최근에 사용한 사이트 및 서버**에 나열되어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-202">If you regularly use reports on a report server, the server might be listed in **Recent Sites and Servers**.</span></span> <span data-ttu-id="5a731-203">그렇지 않으면 이름에 보고서 서버의 주소를 입력하고 **열기** 를 클릭하여 보고서 서버 사이트에서 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-203">Otherwise, in Name, type an address to a report server and click **Open** to browse the folders on the report server site.</span></span> <span data-ttu-id="5a731-204">보고서 서버에 대 한 주소 예는 http:///reportserver 수 있습니다. \<computername></span><span class="sxs-lookup"><span data-stu-id="5a731-204">An example address for a report server might be http://\<computername>/reportserver.</span></span>  
  
5.  <span data-ttu-id="5a731-205">보고서를 선택하고 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-205">Select the report and click **Open**.</span></span> <span data-ttu-id="5a731-206">또는 **이름** 입력란에 전체 경로와 보고서 이름을 포함하여 보고서 링크를 붙여 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-206">Alternatively, you can paste a link to the report, including the full path and report name, in the **Name** text box.</span></span> <span data-ttu-id="5a731-207">테이블 가져오기 마법사를 통해 보고서에 연결되고 미리 보기 영역에서 보고서가 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-207">The Table Import wizard connects to the report and renders it in the preview area.</span></span>  
  
     <span data-ttu-id="5a731-208">보고서에서 매개 변수를 사용하는 경우 매개 변수를 지정해야 하며, 그렇지 않으면 보고서 연결을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-208">If the report uses parameters, you must specify a parameter or you cannot create the report connection.</span></span> <span data-ttu-id="5a731-209">이렇게 하면 매개 변수 값과 관련된 행만 데이터 피드로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-209">When you do so, only the rows related to the parameter value are imported in the data feed.</span></span>  
  
    1.  <span data-ttu-id="5a731-210">보고서에 제공된 목록 상자나 콤보 상자를 사용하여 매개 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-210">Choose a parameter using the list box or combo box provided in the report.</span></span>  
  
    2.  <span data-ttu-id="5a731-211">**보고서 보기** 를 클릭하여 데이터를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-211">Click **View Report** to update the data.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="5a731-212">보고서를 보면 선택한 매개 변수가 데이터 피드 정의와 함께 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-212">Viewing the report saves the parameters that you selected together with the data feed definition.</span></span>  
  
     <span data-ttu-id="5a731-213">필요에 따라 **고급** 을 클릭하여 보고서의 공급자별 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-213">Optionally, click **Advanced** to set provider-specific properties for the report.</span></span>  
  
6.  <span data-ttu-id="5a731-214">**연결 테스트** 를 클릭하여 보고서를 데이터 피드로 사용할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-214">Click **Test Connection** to make sure the report is available as a data feed.</span></span> <span data-ttu-id="5a731-215">또는 **고급** 을 클릭하여 데이터 피드 연결을 지정하는 포함 XML이 **인라인 서비스 문서** 속성에 들어 있는지 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-215">Alternatively, you can also click **Advanced** to confirm that the **Inline Service Document** property contains embedded XML that specifies the data feed connection.</span></span>  
  
7.  <span data-ttu-id="5a731-216">**다음** 을 클릭하여 가져오기 작업을 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-216">Click **Next** to continue with the import.</span></span>  
  
8.  <span data-ttu-id="5a731-217">**가장 정보** 페이지에서 데이터를 새로 고칠 때 Analysis Services가 데이터 원본에 연결하는 데 사용할 자격 증명을 지정하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-217">On the **Impersonation Information** page, specify the credentials that Analysis Services will use to connect to the data source when refreshing the data, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="5a731-218">마법사의 **테이블 및 뷰 선택** 페이지에서 데이터로 가져올 보고서 파트 옆의 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-218">In the **Select Tables and Views** page of the wizard, select the check box next to the report parts that you want to import as data.</span></span>  
  
     <span data-ttu-id="5a731-219">일부 보고서에는 테이블, 목록 또는 그래프를 비롯한 여러 파트가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-219">Some reports can contain multiple parts, including tables, lists, or graphs.</span></span>  
  
10. <span data-ttu-id="5a731-220">**이름** 상자에 모델에서 데이터 피드를 저장할 테이블의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-220">In the **Friendly name** box, type the name of the table where you want the data feed to be saved in your model.</span></span>  
  
     <span data-ttu-id="5a731-221">이름을 할당하지 않은 경우 Reporting Services 컨트롤의 이름(예: Tablix1, Tablix2)이 기본적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-221">The name of the Reporting Service control is used by default if no name has been assigned: for example, Tablix1, Tablix2.</span></span> <span data-ttu-id="5a731-222">가져온 데이터 피드의 원본을 보다 쉽게 식별할 수 있도록 가져올 때 이 이름을 변경하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-222">We recommend that you change this name during import so that you can more easily identify the origin of the imported data feed.</span></span>  
  
11. <span data-ttu-id="5a731-223">**미리 보기 및 필터** 를 클릭하여 데이터를 검토하고 열 선택을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-223">Click **Preview and Filter** to review the data and change column selections.</span></span> <span data-ttu-id="5a731-224">보고서 데이터 피드로 가져오는 행을 제한할 수는 없지만 해당 확인란의 선택을 취소하여 열을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-224">You cannot restrict the rows that are imported in the report data feed, but you can remove columns by clearing the check boxes.</span></span> <span data-ttu-id="5a731-225">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-225">Click **OK**.</span></span>  
  
12. <span data-ttu-id="5a731-226">**테이블 및 뷰 선택** 페이지에서 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a731-226">In the **Select Tables and Views** page, click **Finish**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a731-227">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5a731-227">See Also</span></span>  
 <span data-ttu-id="5a731-228">[SSAS 테이블 형식&#41;&#40;지원 되는 데이터 원본](tabular-models/data-sources-supported-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="5a731-228">[Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md) </span></span>  
 <span data-ttu-id="5a731-229">[SSAS 테이블 형식&#41;&#40;지원 되는 데이터 형식](tabular-models/data-types-supported-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="5a731-229">[Data Types Supported &#40;SSAS Tabular&#41;](tabular-models/data-types-supported-ssas-tabular.md) </span></span>  
 <span data-ttu-id="5a731-230">[가장 &#40;SSAS 테이블 형식&#41;](tabular-models/impersonation-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="5a731-230">[Impersonation &#40;SSAS Tabular&#41;](tabular-models/impersonation-ssas-tabular.md) </span></span>  
 <span data-ttu-id="5a731-231">[SSAS 테이블 형식&#41;&#40;데이터 처리](process-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="5a731-231">[Process Data &#40;SSAS Tabular&#41;](process-data-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="5a731-232">데이터 가져오기&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="5a731-232">Import Data &#40;SSAS Tabular&#41;</span></span>](import-data-ssas-tabular.md)  
  
  

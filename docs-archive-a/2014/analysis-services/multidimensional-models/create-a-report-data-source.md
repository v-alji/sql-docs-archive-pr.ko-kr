---
title: 보고서 데이터 원본 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: bd6662c7-ffbe-479d-8944-3dc858340998
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9205eac497fc047b471f5b80becec36495474d88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737047"
---
# <a name="create-a-report-data-source"></a><span data-ttu-id="1693c-102">보고서 데이터 원본 만들기</span><span class="sxs-lookup"><span data-stu-id="1693c-102">Create a Report Data Source</span></span>
  <span data-ttu-id="1693c-103">파워 뷰를 다차원 모델에 연결하려면 SharePoint 라이브러리에서 .rsds 파일이라는 공유 보고서 데이터 원본 정의를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-103">In order for Power View to connect to a multidimensional model, you must create a shared report data source definition, also known as an .rsds file, in a SharePoint library.</span></span> <span data-ttu-id="1693c-104">.rsds 파일은 다차원 모델에 연결하는 데 사용되는 Analysis Services 서버 인스턴스의 이름, 연결 형식, 연결 문자열 및 자격 증명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-104">The .rsds file specifies the name of an Analysis Services server instance, connection type, connection string, and credentials used to connect to the multidimensional model.</span></span> <span data-ttu-id="1693c-105">사용자가 .rsds를 클릭하면 비어 있는 새 파워 뷰 보고서(.rdlx 파일)가 브라우저에 열립니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-105">When a user clicks on the .rsds, a new blank Power View report (an .rdlx file) opens in the browser.</span></span>  
  
 <span data-ttu-id="1693c-106">.rsds 연결을 만들려면 SQL Server 2012 이상의 Reporting Services와 SharePoint 2010 또는 SharePoint 2013용 Reporting Services 추가 기능을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-106">In order to create an .rsds connection, you must have SQL Server 2012 (or later) Reporting Services and the Reporting Services add-in for SharePoint 2010 or SharePoint 2013 installed.</span></span>  
  
## <a name="create-a-report-data-source-rsds-connection-to-a-multidimensional-model"></a><span data-ttu-id="1693c-107">다차원 모델에 대한 보고서 데이터 원본(.rsds) 연결 만들기</span><span class="sxs-lookup"><span data-stu-id="1693c-107">Create a Report Data Source (.rsds) connection to a multidimensional model</span></span>  
 <span data-ttu-id="1693c-108">시작하기 전에 다음을 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-108">Before you begin, you need to know:</span></span>  
  
-   <span data-ttu-id="1693c-109">다차원 모드에서 실행하는 Analysis Services 서버 인스턴스의 이름.</span><span class="sxs-lookup"><span data-stu-id="1693c-109">The name of the Analysis Services server instance running in Multidimensional mode.</span></span>  
  
-   <span data-ttu-id="1693c-110">연결할 다차원 데이터베이스의 이름.</span><span class="sxs-lookup"><span data-stu-id="1693c-110">The name of the multidimensional database you want to connect to.</span></span>  
  
-   <span data-ttu-id="1693c-111">두 개 이상 있는 경우 큐브의 이름.</span><span class="sxs-lookup"><span data-stu-id="1693c-111">The name of the cube, if there is more than one.</span></span>  
  
-   <span data-ttu-id="1693c-112">(선택 사항) 큐브 뷰 이름.</span><span class="sxs-lookup"><span data-stu-id="1693c-112">(Optional) Perspective name.</span></span>  
  
-   <span data-ttu-id="1693c-113">(선택 사항) 로캘 식별자.</span><span class="sxs-lookup"><span data-stu-id="1693c-113">(Optional) Locale Identifier.</span></span>  
  
#### <a name="to-create-a-shared-report-data-source-rsds-file-sharepoint-2010"></a><span data-ttu-id="1693c-114">공유 데이터 원본(.rsds) 파일을 만들려면(SharePoint 2010)</span><span class="sxs-lookup"><span data-stu-id="1693c-114">To create a shared Report Data Source (.rsds) file (SharePoint 2010)</span></span>  
  
1.  <span data-ttu-id="1693c-115">라이브러리 리본 메뉴에 있는 **문서** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-115">Click the **Documents** tab on the library ribbon.</span></span>  
  
2.  <span data-ttu-id="1693c-116">**새 문서**  >  **보고서 데이터 원본**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-116">Click **New Document** > **Report Data Source**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1693c-117">메뉴에 **보고서 데이터 원본** 항목이 표시되지 않는 경우 이 라이브러리에 대해 보고서 데이터 원본의 콘텐츠 형식이 설정되어 있지 않은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-117">If you do not see the **Report Data Source** item on the menu, the report data source content type has not been enabled for this library.</span></span> <span data-ttu-id="1693c-118">자세한 내용은 [SharePoint 통합 모드&#41;에서 &#40;Reporting Services 라이브러리에 보고서 서버 콘텐츠 형식 추가 ](../../reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1693c-118">For more information, see [Add Report Server Content Types to a Library &#40;Reporting Services in SharePoint Integrated Mode&#41;](../../reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md).</span></span>  
  
3.  <span data-ttu-id="1693c-119">**데이터 원본 속성** 페이지에서 **이름**에 연결 .rsds 파일의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-119">On the **Data Source Properties** page, in **Name**, type a name for the connection .rsds file.</span></span>  
  
4.  <span data-ttu-id="1693c-120">**데이터 원본 유형**에서 **파워 뷰용 Microsoft BI 의미 체계 모델**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-120">In **Data Source Type**, select **Microsoft BI Semantic Model for Power View**.</span></span>  
  
5.  <span data-ttu-id="1693c-121">**연결 문자열**에서 Analysis Services 서버 이름, 데이터베이스 이름, 큐브 이름 및 선택적 설정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-121">In **Connection String**, specify the Analysis Services server name, database name, cube name, and any optional settings.</span></span>  
  
     <span data-ttu-id="1693c-122">연결 문자열: `Data source=<servername>;initial catalog=<multidimensionaldatabasename>-ee;cube='<cubename>'`</span><span class="sxs-lookup"><span data-stu-id="1693c-122">Connection String: `Data source=<servername>;initial catalog=<multidimensionaldatabasename>-ee;cube='<cubename>'`</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1693c-123">큐브가 두 개 이상 있는 경우 큐브 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-123">If there is more than one cube, you must specify a cube name.</span></span>  
  
     <span data-ttu-id="1693c-124">(선택 사항) 큐브에는 특정 차원 및/또는 측정값 그룹만 클라이언트에 표시되는 선택 뷰를 사용자에게 제공하는 큐브 뷰가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-124">(Optional) Cubes can have perspectives that provide users a select view where only certain dimensions and/or measure groups are visible in the client.</span></span> <span data-ttu-id="1693c-125">큐브 뷰를 지정하려면 큐브 뷰 이름을 Cube 속성에 대한 값으로 지정합니다. `Data source=<servername>;initial catalog=<multidimensionaldatabasename>-ee;cube='<perspectivename>'`</span><span class="sxs-lookup"><span data-stu-id="1693c-125">To specify a perspective, enter the perspective name as a value to the Cube property: `Data source=<servername>;initial catalog=<multidimensionaldatabasename>-ee;cube='<perspectivename>'`</span></span>  
  
     <span data-ttu-id="1693c-126">(선택 사항) 큐브에는 모델 내의 다양한 언어에 대해 지정된 메타데이터 및 데이터 번역이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-126">(Optional) Cubes can have metadata and data translations specified for various languages within the model.</span></span> <span data-ttu-id="1693c-127">번역 (데이터 및 메타 데이터)을 보려면 연결 문자열에 "로캘 식별자" 속성을 추가 해야 합니다.`Data source=<servername>;initial catalog=<multidimensionaldatabasename>-ee;cube='<cubename>'; Locale Identifier=<identifier number>`</span><span class="sxs-lookup"><span data-stu-id="1693c-127">In order to see the translations (data and metadata) you need to add the "Locale Identifier" property to the connection string: `Data source=<servername>;initial catalog=<multidimensionaldatabasename>-ee;cube='<cubename>'; Locale Identifier=<identifier number>`</span></span>  
  
6.  <span data-ttu-id="1693c-128">**자격 증명**에서 보고서 서버가 외부 데이터 원본에 액세스하는 데 필요한 자격 증명을 얻는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-128">In **Credentials**, specify how the report server obtains credentials to access the external data source.</span></span>  
  
    -   <span data-ttu-id="1693c-129">보고서를 연 사용자의 자격 증명을 사용하여 데이터에 액세스하려면 **Windows 인증(통합)** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-129">Select **Windows authentication (integrated)** if you want to access the data using the credentials of the user who opened the report.</span></span> <span data-ttu-id="1693c-130">SharePoint 사이트 또는 팜에서 폼 인증을 사용하거나 트러스트된 계정을 통해 보고서 서버에 연결하는 경우 이 옵션을 선택하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="1693c-130">Do not select this option if the SharePoint site or farm uses forms authentication or connects to the report server through a trusted account.</span></span> <span data-ttu-id="1693c-131">이 보고서에 대한 구독 또는 데이터 처리를 예약하려는 경우 이 옵션을 선택하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="1693c-131">Do not select this option if you want to schedule subscription or data processing for this report.</span></span> <span data-ttu-id="1693c-132">이 옵션은 도메인에 Kerberos 인증을 설정한 경우나 데이터 원본이 보고서 서버와 같은 컴퓨터에 있는 경우에 가장 잘 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-132">This option works best when Kerberos authentication is enabled for your domain, or when the data source is on the same computer as the report server.</span></span> <span data-ttu-id="1693c-133">Kerberos 인증을 해제하면 Windows 자격 증명이 하나의 다른 컴퓨터로만 전달될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-133">If Kerberos authentication is not enabled, Windows credentials can only be passed to one other computer.</span></span> <span data-ttu-id="1693c-134">따라서 추가 연결이 필요한 다른 컴퓨터에 외부 데이터 원본이 있는 경우 원하는 데이터 대신 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-134">This means that if the external data source is on another computer, requiring an additional connection, you will get an error instead of the data you expect.</span></span>  
  
    -   <span data-ttu-id="1693c-135">사용자가 보고서를 실행할 때마다 자격 증명을 입력하도록 하려면 **자격 증명 확인** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-135">Select **Prompt for credentials** if you want the user to enter his or her credentials each time he or she runs the report.</span></span> <span data-ttu-id="1693c-136">이 보고서에 대한 구독 또는 데이터 처리를 예약하려는 경우 이 옵션을 선택하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="1693c-136">Do not select this option if you want to schedule subscription or data processing for this report.</span></span>  
  
    -   <span data-ttu-id="1693c-137">단일 자격 증명 집합을 사용하여 데이터에 액세스하려면 **저장된 자격 증명** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-137">Select **Stored credentials** if you want to access the data using a single set of credentials.</span></span> <span data-ttu-id="1693c-138">자격 증명은 저장되기 전에 암호화됩니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-138">The credentials are encrypted before they are stored.</span></span> <span data-ttu-id="1693c-139">저장된 자격 증명의 인증 방법을 결정하는 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-139">You can select options that determine how the stored credentials are authenticated.</span></span> <span data-ttu-id="1693c-140">저장된 자격 증명이 Windows 사용자 계정에 속하면 Windows 자격 증명으로 사용을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-140">Select Use as Windows credentials if the stored credentials belong to a Windows user account.</span></span> <span data-ttu-id="1693c-141">데이터베이스 서버에 대한 실행 컨텍스트를 설정하려면 **이 계정에 대한 실행 컨텍스트 설정** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-141">Select **Set execution context to this account** if you want to set the execution context on the database server.</span></span>  
  
    -   <span data-ttu-id="1693c-142">연결 문자열에서 자격 증명을 지정하거나 최소 권한 계정을 사용하여 보고서를 실행하려면 **자격 증명 필요 없음** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-142">Select **Credentials are not required** if you specify credentials in the connection string, or if you want to run the report using a least-privilege account.</span></span>  
  
7.  <span data-ttu-id="1693c-143">**연결 테스트** 를 클릭하여 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-143">Click **Test Connection** to validate.</span></span>  
  
8.  <span data-ttu-id="1693c-144">데이터 원본을 활성화 하려면 **이 데이터 원본 사용** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-144">Select **Enable this data source** if you want the data source to be active.</span></span> <span data-ttu-id="1693c-145">데이터 원본이 구성되었지만 활성이 아닌 경우 사용자가 보고서를 만들려고 하면 오류 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1693c-145">If the data source is configured but not active, users will receive an error message when they attempt to create a report.</span></span>  
  
  

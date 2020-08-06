---
title: 보고서의 데이터 원본 속성 구성(보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data sources [Reporting Services], embedded
ms.assetid: 27af5195-c845-40e0-9a9c-efe569424022
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 42969b4667dd71e4c6413f38e4deadb96491169c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647455"
---
# <a name="configure-data-source-properties-for-a-report--report-manager"></a><span data-ttu-id="2a663-102">보고서의 데이터 원본 속성 구성(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="2a663-102">Configure Data Source Properties for a Report  (Report Manager)</span></span>
  <span data-ttu-id="2a663-103">보고서를 실행하면 보고서 서버가 속성 정보를 검색하여 데이터 원본에 연결하는 방식을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="2a663-103">When you run a report, the report server retrieves property information to determine how to connect to a data source.</span></span> <span data-ttu-id="2a663-104">데이터 원본 유형, 연결 문자열 및 자격 증명 정보가 게시된 보고서의 데이터 원본 속성 페이지에 지정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a663-104">The data source type, connection string, and credential information are specified in the Data Source property pages of the published report.</span></span> <span data-ttu-id="2a663-105">데이터 원본 연결 정보가 보고서 생성 시 지정된 원래 값과 달라지도록 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a663-105">You can set the properties to vary the data source connection information from the original values that were specified when the report was created.</span></span>  
  
 <span data-ttu-id="2a663-106">사용할 연결 정보를 지정하는 미리 정의된 공유 데이터 원본이 있는 경우 이 공유 데이터 원본을 대신 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a663-106">Alternatively, if you have a predefined shared data source that already specifies the connection information you want to use, you can specify a shared data source instead.</span></span> <span data-ttu-id="2a663-107">공유 데이터 원본을 사용하려면 보고서의 데이터 원본 속성 페이지에서 **공유 데이터 원본** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2a663-107">To use a shared data source, click **A shared data source** on the Data Source properties page of the report.</span></span>  
  
### <a name="to-configure-an-embedded-data-source"></a><span data-ttu-id="2a663-108">포함된 데이터 원본을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="2a663-108">To configure an embedded data source</span></span>  
  
1.  <span data-ttu-id="2a663-109">[보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md)를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2a663-109">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="2a663-110">보고서 관리자에서 **내용** 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="2a663-110">In Report Manager, navigate to the **Contents** page.</span></span> <span data-ttu-id="2a663-111">보고서별 데이터 원본을 구성할 보고서로 이동한 후 해당 보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2a663-111">Navigate to the report that you want to configure a report-specific data source for, and open the report.</span></span>  
  
3.  <span data-ttu-id="2a663-112">**속성** 탭을 클릭 합니다. **일반** 속성 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="2a663-112">Click the **Properties** tab. The **General** properties page opens.</span></span>  
  
4.  <span data-ttu-id="2a663-113">**데이터 원본** 탭을 클릭 합니다. 그러면 보고서의 데이터 원본 속성 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="2a663-113">Click the **Data Sources** tab. This opens the Data Source properties page of the report.</span></span>  
  
5.  <span data-ttu-id="2a663-114">보고서 내의 데이터 원본 연결 정보를 지정하려면 **사용자 지정 데이터 원본** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2a663-114">Click **A custom data source** to specify data source connection information within the report.</span></span>  
  
6.  <span data-ttu-id="2a663-115">**연결 형식** 목록에서 데이터 원본의 데이터를 처리하는 데 사용할 데이터 처리 확장 프로그램을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2a663-115">In the **Connection Type** list, specify the data processing extension that is used to process data from the data source.</span></span>  
  
7.  <span data-ttu-id="2a663-116">**연결 문자열**에는 보고서 서버가 데이터 원본에 연결 하는 데 사용 하는 연결 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a663-116">For **Connection String**, specify the connection string that the report server uses to connect to the data source.</span></span> <span data-ttu-id="2a663-117">연결 문자열에는 자격 증명을 지정하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2a663-117">It is recommended that you do not specify credentials in the connection string.</span></span>  
  
     <span data-ttu-id="2a663-118">다음 예에서는 로컬 데이터베이스에 연결 하기 위한 연결 문자열을 보여 줍니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2a663-118">The following example illustrates a connection string for connecting to the local [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database:</span></span>  
  
    ```  
    data source=<localservername>; initial catalog=AdventureWorks2012  
    ```  
  
8.  <span data-ttu-id="2a663-119">**연결 방법**에서 보고서를 실행할 때 자격 증명을 가져오는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2a663-119">For **Connect using**, specify how credentials are obtained when the report runs:</span></span>  
  
    -   <span data-ttu-id="2a663-120">로그온 이름과 암호를 입력하라는 메시지를 표시하려면 **보고서를 실행하는 사용자가 제공한 자격 증명**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2a663-120">If you want to prompt the user for a logon name and password, click **Credentials supplied by the user running the report**.</span></span>  
  
    -   <span data-ttu-id="2a663-121">자동화된 보고서 기록 생성과 같은 예약된 작업이나 구독을 지원하는 보고서에 데이터 원본을 사용하려면 **보고서 서버에 안전하게 저장된 자격 증명**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2a663-121">If you intend to use the data source with reports that support subscriptions or other scheduled operations (such as automated report history generation), click **Credentials stored securely in the report server**.</span></span>  
  
    -   <span data-ttu-id="2a663-122">보고서 서버가 보고서에 액세스하는 사용자의 자격 증명을 외부 데이터 원본을 호스팅하는 서버에 전달하도록 하려면 **Windows 통합 보안**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2a663-122">If you want the report server to pass the credentials of the user accessing the report to the server hosting the external data source, click **Windows Integrated Security**.</span></span> <span data-ttu-id="2a663-123">이 경우 사용자 이름이나 암호를 입력하라는 메시지가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2a663-123">In this case, the user is not prompted to type a user name or password.</span></span>  
  
    -   <span data-ttu-id="2a663-124">데이터 원본이 파일 시스템에서 액세스되는 XML 파일인 경우와 같이 데이터 원본이 자격 증명을 사용하지 않는 경우 **자격 증명 필요 없음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2a663-124">If the data source does not use credentials (for example, if the data source is an XML file that is accessed from the file system), click **Credentials are not required**.</span></span> <span data-ttu-id="2a663-125">이 자격 증명 유형은 데이터 원본에 대해 유효한 경우에만 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a663-125">You should only specify this credential type if it is valid for the data source.</span></span> <span data-ttu-id="2a663-126">인증이 필요한 데이터 원본에 대해 이 옵션을 선택하면 연결이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="2a663-126">If you select this option for a data source that requires authentication, the connection will fail.</span></span> <span data-ttu-id="2a663-127">이 옵션을 선택할 때는 사용자 자격 증명을 사용할 수 없는 경우 보고서 서버가 다른 컴퓨터에 연결하여 데이터나 파일을 검색할 수 있도록 허용하는 무인 실행 계정을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a663-127">If you select this option, be sure to configure the unattended execution account that allows the report server to connect to other computers to retrieve data or files when user credentials are not available.</span></span>  
  
 <span data-ttu-id="2a663-128">자격 증명 구성 방법에 대한 자세한 내용은 [보고서 데이터 원본에 대한 자격 증명 및 연결 정보 지정](specify-credential-and-connection-information-for-report-data-sources.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a663-128">For more information about configuring credentials, see [Specify Credential and Connection Information for Report Data Sources](specify-credential-and-connection-information-for-report-data-sources.md).</span></span> <span data-ttu-id="2a663-129">무인 실행 계정에 대한 자세한 내용은 [무인 실행 계정 구성&#40;SSRS 구성 관리자&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2a663-129">For more information about the unattended execution account, see [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a663-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2a663-130">See Also</span></span>  
 <span data-ttu-id="2a663-131">[내용 페이지 &#40;보고서 관리자&#41;](../contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="2a663-131">[Contents Page &#40;Report Manager&#41;](../contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="2a663-132">[새 데이터 원본 페이지 &#40;보고서 관리자&#41;](../new-data-source-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="2a663-132">[New Data Source Page &#40;Report Manager&#41;](../new-data-source-page-report-manager.md) </span></span>  
 <span data-ttu-id="2a663-133">[SSRS&#41;&#40;공유 데이터 원본 만들기, 수정 및 삭제](create-modify-and-delete-shared-data-sources-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2a663-133">[Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md) </span></span>  
 <span data-ttu-id="2a663-134">[보고서 데이터 원본 관리](manage-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="2a663-134">[Manage Report Data Sources](manage-report-data-sources.md) </span></span>  
 <span data-ttu-id="2a663-135">[공유 데이터 원본 &#40;보고서 관리자 만들기, 삭제 또는 수정&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="2a663-135">[Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) </span></span>  
 [<span data-ttu-id="2a663-136">데이터 원본 속성 페이지&#40;보고서 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="2a663-136">Data Sources Properties Page &#40;Report Manager&#41;</span></span>](../data-sources-properties-page-report-manager.md)  
  
  

---
title: 공유 데이터 원본 만들기, 삭제 또는 수정 (보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- shared data sources [Reporting Services]
- removing shared data sources
- data sources [Reporting Services], shared
- deleting shared data sources
- modifying shared data sources
ms.assetid: cd7bace3-f8ec-4ee3-8a9f-2f217cdca9f2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6f4ff658e656b159995087df3121806b462e687
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651548"
---
# <a name="create-delete-or-modify-a-shared-data-source-report-manager"></a><span data-ttu-id="f6a75-102">공유 데이터 원본 만들기, 삭제 및 수정(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="f6a75-102">Create, Delete, or Modify a Shared Data Source (Report Manager)</span></span>
  <span data-ttu-id="f6a75-103">공유 데이터 원본은 데이터 원본에 대한 연결 속성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-103">A shared data source specifies connection properties for a data source.</span></span> <span data-ttu-id="f6a75-104">많은 보고서, 모델 또는 데이터 기반 구독에서 사용되는 데이터 원본이 있는 경우 여러 위치에서 같은 연결 정보를 유지 관리해야 하는 오버헤드를 없애기 위해 공유 데이터 원본을 만드십시오.</span><span class="sxs-lookup"><span data-stu-id="f6a75-104">If you have a data source that is used by a large number of reports, models, or data-driven subscriptions, consider creating a shared data source to eliminate the overhead of having to maintain the same connection information in multiple places.</span></span>  
  
 <span data-ttu-id="f6a75-105">다음 아이콘은 보고서 관리자 폴더 계층의 공유 데이터 원본을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-105">The following icon indicates a shared data source in the Report Manager folder hierarchy:</span></span>  
  
 <span data-ttu-id="f6a75-106">![공유 데이터 원본 아이콘](media/hlp-16datasource.png "공유 데이터 원본 아이콘")</span><span class="sxs-lookup"><span data-stu-id="f6a75-106">![Shared data source icon](media/hlp-16datasource.png "Shared data source icon")</span></span>  
<span data-ttu-id="f6a75-107">공유 데이터 원본 아이콘</span><span class="sxs-lookup"><span data-stu-id="f6a75-107">shared data source icon</span></span>  
  
### <a name="to-create-a-shared-data-source"></a><span data-ttu-id="f6a75-108">공유 데이터 원본을 만들려면</span><span class="sxs-lookup"><span data-stu-id="f6a75-108">To create a shared data source</span></span>  
  
1.  <span data-ttu-id="f6a75-109">[보고서 관리자&#40;SSRS 기본 모드&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-109">Start [Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="f6a75-110">보고서 관리자에서 **내용** 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-110">In Report Manager, navigate to the **Contents** page.</span></span>  
  
3.  <span data-ttu-id="f6a75-111">**새 데이터 원본**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-111">Click **New Data Source**.</span></span> <span data-ttu-id="f6a75-112">**새 데이터 원본** 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-112">The **New Data Source** page opens.</span></span>  
  
4.  <span data-ttu-id="f6a75-113">항목의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-113">Type a name for the item.</span></span> <span data-ttu-id="f6a75-114">이름은 한 글자 이상이어야 하며 문자로 시작되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-114">A name must contain at least one character and it must start with a letter.</span></span> <span data-ttu-id="f6a75-115">특정 기호도 포함할 수 있지만 공백 또는 ; ?</span><span class="sxs-lookup"><span data-stu-id="f6a75-115">It can also include certain symbols, but not spaces or the characters ; ?</span></span> <span data-ttu-id="f6a75-116">: \@ & = +, $/\* \< > | " /.</span><span class="sxs-lookup"><span data-stu-id="f6a75-116">: \@ & = + , $ / \* \< > | " /.</span></span>  
  
5.  <span data-ttu-id="f6a75-117">연결 정보를 제공하는 설명을 입력합니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="f6a75-117">Optionally type a description to provide users with information about the connection.</span></span> <span data-ttu-id="f6a75-118">이 설명은 보고서 관리자의 **내용** 페이지에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-118">This description will appear on the **Contents** page in Report Manager.</span></span>  
  
6.  <span data-ttu-id="f6a75-119">**데이터 원본 유형** 목록에서 데이터 원본의 데이터를 처리하는 데 사용할 데이터 처리 확장 프로그램을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-119">In the **Data source type** list, specify the data processing extension that is used to process data from the data source.</span></span>  
  
7.  <span data-ttu-id="f6a75-120">**연결 문자열**에는 보고서 서버가 데이터 원본에 연결하는 데 사용하는 연결 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-120">For **Connection string**, specify the connection string that the report server uses to connect to the data source.</span></span> <span data-ttu-id="f6a75-121">연결 문자열에는 자격 증명을 지정하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-121">It is recommended that you do not specify credentials in the connection string.</span></span>  
  
     <span data-ttu-id="f6a75-122">다음 예에서는 로컬 데이터베이스에 연결 하기 위한 연결 문자열을 보여 줍니다 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f6a75-122">The following example illustrates a connection string for connecting to the local [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database:</span></span>  
  
    ```  
    data source=<localservername>; initial catalog=AdventureWorks2012  
    ```  
  
8.  <span data-ttu-id="f6a75-123">**연결 방법**에서 보고서를 실행할 때 자격 증명을 가져오는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-123">For **Connect using**, specify how credentials are obtained when the report runs:</span></span>  
  
    -   <span data-ttu-id="f6a75-124">로그온 이름과 암호를 입력하라는 메시지를 표시하려면 **보고서를 실행하는 사용자가 제공한 자격 증명**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-124">If you want to prompt the user for a logon name and password, click **Credentials supplied by the user running the report**.</span></span> <span data-ttu-id="f6a75-125">사용자가 Windows 자격 증명으로 입력한 자격 증명을 사용하려면 **데이터 원본에 연결할 때 Windows 자격 증명으로 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-125">To use the credentials that the user enters as Windows credentials, click **Use as Windows credentials when connecting to the data source**.</span></span> <span data-ttu-id="f6a75-126">사용자 이름과 암호가 데이터베이스 자격 증명인 경우 이 옵션을 선택하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="f6a75-126">If the user name and password are database credentials, do not select this option.</span></span>  
  
    -   <span data-ttu-id="f6a75-127">데이터 원본을 해당 소유자가 관리하는 저장된 자격 증명을 포함하는 공유 데이터 원본으로 사용하거나 자동화된 보고서 기록 생성과 같은 예약된 다른 작업이나 구독을 지원하는 보고서에 사용하려면 **보고서 서버에 안전하게 저장된 자격 증명**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-127">If you intend to use the data source as a shared data source with saved credentials that are managed by the owner of the data source, or for reports that support subscriptions or other scheduled operations (such as automated report history generation), click **Credentials stored securely in the report server**.</span></span> <span data-ttu-id="f6a75-128">데이터베이스 서버가 가장 또는 위임을 지원하는 경우에는 **데이터 원본에 연결한 후 인증된 사용자로 가장**을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-128">If the database server supports impersonation or delegation, you can select **Impersonate the authenticated user after a connection has been made to the data source**.</span></span>  
  
    -   <span data-ttu-id="f6a75-129">보고서 서버가 보고서에 액세스하는 사용자의 자격 증명을 외부 데이터 원본을 호스팅하는 서버에 전달하도록 하려면 **Windows 통합 보안**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-129">If you want the report server to pass the credentials of the user accessing the report to the server hosting the external data source, click **Windows Integrated Security**.</span></span> <span data-ttu-id="f6a75-130">이 경우 사용자 이름이나 암호를 입력하라는 메시지가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-130">In this case, the user is not prompted to type a user name or password.</span></span>  
  
    -   <span data-ttu-id="f6a75-131">데이터 원본이 파일 시스템에서 액세스되는 XML 파일인 경우와 같이 데이터 원본이 자격 증명을 사용하지 않는 경우 **자격 증명 필요 없음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-131">If the data source does not use credentials (for example, if the data source is an XML file that is accessed from the file system), click **Credentials are not required**.</span></span> <span data-ttu-id="f6a75-132">이 자격 증명 유형은 데이터 원본에 대해 유효한 경우에만 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-132">You should only specify this credential type if it is valid for the data source.</span></span> <span data-ttu-id="f6a75-133">인증이 필요한 데이터 원본에 대해 이 옵션을 선택하면 연결이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-133">If you select this option for a data source that requires authentication, the connection will fail.</span></span> <span data-ttu-id="f6a75-134">이 옵션을 선택할 때는 사용자 자격 증명을 사용할 수 없는 경우 보고서 서버가 다른 컴퓨터에 연결하여 데이터나 파일을 검색할 수 있도록 허용하는 무인 실행 계정을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-134">If you select this option, be sure to configure the unattended execution account that allows the report server to connect to other computers to retrieve data or files when user credentials are not available.</span></span>  
  
     <span data-ttu-id="f6a75-135">자격 증명 구성 방법에 대한 자세한 내용은 [보고서 데이터 원본에 대한 자격 증명 및 연결 정보 지정](report-data/specify-credential-and-connection-information-for-report-data-sources.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f6a75-135">For more information about configuring credentials, see [Specify Credential and Connection Information for Report Data Sources](report-data/specify-credential-and-connection-information-for-report-data-sources.md).</span></span> <span data-ttu-id="f6a75-136">무인 실행 계정에 대한 자세한 내용은 [무인 실행 계정 구성&#40;SSRS 구성 관리자&#41;](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f6a75-136">For more information about the unattended execution account, see [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).</span></span>  
  
9. <span data-ttu-id="f6a75-137">**연결 테스트** 단추를 클릭하여 데이터 원본 구성의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-137">Click the **Test Connection** button to validate the data source configuration.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f6a75-138">XML 데이터 원본 유형에서는 연결 테스트 단추를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-138">The Test Connection button is not supported for the XML data source type.</span></span>  
  
10. <span data-ttu-id="f6a75-139">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-139">Click **OK**</span></span>  
  
### <a name="to-modify-a-shared-data-source"></a><span data-ttu-id="f6a75-140">공유 데이터 원본을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="f6a75-140">To modify a shared data source</span></span>  
  
1.  <span data-ttu-id="f6a75-141">보고서 관리자에서 내용 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-141">In Report Manager, navigate to the Contents page.</span></span>  
  
2.  <span data-ttu-id="f6a75-142">공유 데이터 원본 항목으로 이동하고 항목을 마우스로 가리킨 다음 드롭다운 목록을 클릭하고 상황에 맞는 메뉴에서 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-142">Navigate to the shared data source item, hover over the item, click the drop-down list, and from the context menu, click **Manage**.</span></span> <span data-ttu-id="f6a75-143">**속성** 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-143">The **Properties** page opens.</span></span>  
  
3.  <span data-ttu-id="f6a75-144">데이터 원본을 수정한 후 **적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-144">Modify the data source, and then click **Apply**.</span></span>  
  
### <a name="to-delete-a-shared-data-source"></a><span data-ttu-id="f6a75-145">공유 데이터 원본을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="f6a75-145">To delete a shared data source</span></span>  
  
-   <span data-ttu-id="f6a75-146">보고서 관리자에서 **내용** 페이지로 이동한 후 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-146">In Report Manager, navigate to the **Contents** page and do one of the following:</span></span>  
  
    -   <span data-ttu-id="f6a75-147">공유 데이터 원본 항목으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-147">Navigate to the shared data source item.</span></span>  
  
         <span data-ttu-id="f6a75-148">항목을 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-148">Click the item to open it.</span></span> <span data-ttu-id="f6a75-149">일반 속성 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-149">The General Properties page opens.</span></span>  
  
         <span data-ttu-id="f6a75-150">**삭제**를 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-150">Click **Delete**, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="f6a75-151">**내용** 페이지에서 삭제할 데이터 원본이 들어 있는 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-151">In the **Contents** page, navigate to the folder that contains the data source you want to delete.</span></span>  
  
         <span data-ttu-id="f6a75-152">항목을 마우스로 가리키고 드롭다운 목록을 클릭한 다음 상황에 맞는 메뉴에서 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a75-152">Hover over the item, click the drop-down list, and from the context menu, click **Delete**.</span></span>  
  
         [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f6a75-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f6a75-153">See Also</span></span>  
 <span data-ttu-id="f6a75-154">[Reporting Services의 데이터 연결, 데이터 원본 및 연결 문자열](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="f6a75-154">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 <span data-ttu-id="f6a75-155">[내용 페이지 &#40;보고서 관리자&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="f6a75-155">[Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="f6a75-156">[SSRS&#41;&#40;공유 데이터 원본 만들기, 수정 및 삭제](report-data/create-modify-and-delete-shared-data-sources-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f6a75-156">[Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](report-data/create-modify-and-delete-shared-data-sources-ssrs.md) </span></span>  
 <span data-ttu-id="f6a75-157">[보고서 데이터 원본 관리](report-data/manage-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="f6a75-157">[Manage Report Data Sources](report-data/manage-report-data-sources.md) </span></span>  
 [<span data-ttu-id="f6a75-158">보고서의 데이터 원본 속성 구성&#40;보고서 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="f6a75-158">Configure Data Source Properties for a Report  &#40;Report Manager&#41;</span></span>](report-data/configure-data-source-properties-for-a-report-report-manager.md)  
  
  

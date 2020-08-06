---
title: Reporting Services에 대한 클라이언트 쪽 인쇄 기능 설정 및 해제 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0e709c96-7517-4547-8ef6-5632f8118524
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 031a7cd9b5da07b03b76b6bf49db63572a8fe546
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652575"
---
# <a name="enable-and-disable-client-side-printing-for-reporting-services"></a><span data-ttu-id="522ac-102">Reporting Services에 대한 클라이언트 쪽 인쇄 기능 설정 및 해제</span><span class="sxs-lookup"><span data-stu-id="522ac-102">Enable and Disable Client-Side Printing for Reporting Services</span></span>
  <span data-ttu-id="522ac-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]ActiveX 컨트롤인 **RSClientPrint**는 브라우저에 표시 되는 보고서에 대 한 클라이언트 쪽 인쇄 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX control, **RSClientPrint**, provides client-side printing for reports viewed in a browser.</span></span> <span data-ttu-id="522ac-104">이 컨트롤은 다른 인쇄 대화 상자에 공통적인 기능을 지원하는 사용자 지정 인쇄 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-104">The control displays a custom print dialog box that supports features common to other print dialog boxes.</span></span> <span data-ttu-id="522ac-105">인쇄 미리 보기, 특정 페이지와 범위 지정을 위한 페이지 선택, 페이지 여백 및 방향이 여기에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-105">The features include print preview, page selections for specifying specific pages and ranges, page margins, and orientation.</span></span> <span data-ttu-id="522ac-106">클라이언트 쪽 인쇄 기능은 기본적으로 설정되어 있지만 이 기능을 사용하지 않으려면 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-106">Although client-side printing is enabled by default, you can disable the feature to prevent it from being used.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="522ac-107">ActiveX 컨트롤을 다운로드하려면 관리자 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-107">Downloading ActiveX controls requires administrator permissions.</span></span>  
  
## <a name="downloading-the-activex-control"></a><span data-ttu-id="522ac-108">AcitveX 컨트롤 다운로드</span><span class="sxs-lookup"><span data-stu-id="522ac-108">Downloading the ActiveX Control</span></span>  
 <span data-ttu-id="522ac-109">인쇄 기능을 사용하려는 사용자는 클라이언트 인쇄 기능을 제공하는 ActiveX 컨트롤을 다운로드하여 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-109">Each user who wants to use the print feature must download and install the ActiveX control that provides client print functionality.</span></span> <span data-ttu-id="522ac-110">사용자가 처음으로 보고서 도구 모음에서 **프린터** 아이콘을 클릭 하면 Microsoft ActiveX 컨트롤이 컴퓨터에 다운로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-110">The first time a user clicks the **Printer** icon on the report toolbar, the Microsoft ActiveX control is downloaded to the computer.</span></span> <span data-ttu-id="522ac-111">컨트롤이 다운로드 되 면 사용자가 **프린터** 아이콘을 클릭할 때마다 **인쇄** 대화 상자가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-111">After the control is downloaded, the **Print** dialog box displays whenever the user clicks the **Printer** icon.</span></span>  
  
 <span data-ttu-id="522ac-112">브라우저 설정에 따라 컨트롤을 설치하라는 메시지가 표시되거나 컨트롤을 설치할 수 없거나 컨트롤이 백그라운드에 이미 설치되어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-112">Depending on browser settings, the user may be prompted to install the control, be prevented from installing the control, or have the control install transparently in the background.</span></span>  
  
 <span data-ttu-id="522ac-113">[!INCLUDE[msCoName](../../includes/msconame-md.md)]Internet Explorer의 경우 activex 컨트롤 다운로드 및 설치에 영향을 주는 설정은 웹 콘텐츠 영역에 대 한 **보안 설정** 페이지의 **activex 컨트롤 및 플러그** 인 노드를 통해 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-113">For [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer, settings that affect ActiveX control download and installation are specified through the **ActiveX controls and plug-ins** node in the **Security Settings** page for the Web content zone.</span></span> <span data-ttu-id="522ac-114">웹 영역 보안 기본 설정을 기반으로 사용자가 인쇄 컨트롤을 다운로드하고 실행할 수 있는지 여부는 다음 설정에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-114">The following settings determine whether users can download and run the print control, based on Web zone security preferences:</span></span>  
  
-   <span data-ttu-id="522ac-115">서명된 AcitveX 컨트롤 다운로드</span><span class="sxs-lookup"><span data-stu-id="522ac-115">Download signed ActiveX controls.</span></span>  
  
-   <span data-ttu-id="522ac-116">안전한 것으로 표시된 ActiveX 컨트롤 스크립트</span><span class="sxs-lookup"><span data-stu-id="522ac-116">Script ActiveX controls marked safe for scripting.</span></span>  
  
-   <span data-ttu-id="522ac-117">ActiveX 컨트롤 및 플러그 인 실행</span><span class="sxs-lookup"><span data-stu-id="522ac-117">Run ActiveX controls and plug-ins.</span></span>  
  
 <span data-ttu-id="522ac-118">**RSClientPrint** 를 사용 하 여 클라이언트 쪽 인쇄를 수행 하려는 사용자는 다음을 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-118">Users who want to use **RSClientPrint** to perform client-side printing must enable the following:</span></span>  
  
-   <span data-ttu-id="522ac-119">**서명 된 activex 컨트롤을 다운로드** 하 고 설치를 위해 **스크립팅에 안전한 것으로 표시 된 activex 컨트롤 스크립트** 를 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-119">**Download signed ActiveX controls** and **Script ActiveX control marked safe for scripting** for installation purposes.</span></span>  
  
-   <span data-ttu-id="522ac-120">실행 중인 인쇄 작업을 위해 **ActiveX 컨트롤 및 플러그** 인을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-120">**Run ActiveX controls and plug-ins** for ongoing print operations.</span></span>  
  
 <span data-ttu-id="522ac-121">**RSClientPrint** ActiveX 컨트롤은 서명 됩니다. 즉,의 유효한 디지털 인증서가 포함 되어 있습니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="522ac-121">The **RSClientPrint** ActiveX control is signed, meaning it contains a valid digital certificate from [!INCLUDE[msCoName](../../includes/msconame-md.md)].</span></span>  
  
## <a name="enabling-and-disabling-client-side-printing"></a><span data-ttu-id="522ac-122">클라이언트 쪽 인쇄 기능 설정 및 해제</span><span class="sxs-lookup"><span data-stu-id="522ac-122">Enabling and Disabling Client-Side Printing</span></span>  
 <span data-ttu-id="522ac-123">보고서 서버 관리자는 보고서 서버 시스템 속성 **EnableClientPrinting** 을로 설정 하 여 인쇄 기능을 해제 하는 옵션을 사용할 수 있습니다 `false` .</span><span class="sxs-lookup"><span data-stu-id="522ac-123">Report server administrators have the option of disabling the print feature by setting the report server system property **EnableClientPrinting** to `false`.</span></span> <span data-ttu-id="522ac-124">이렇게 하면 해당 서버에서 관리하는 모든 보고서에 대한 클라이언트 쪽 인쇄 기능이 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-124">This will disable client-side printing for all reports managed by that server.</span></span> <span data-ttu-id="522ac-125">기본적으로 **EnableClientPrinting** 는로 설정 됩니다 `true` .</span><span class="sxs-lookup"><span data-stu-id="522ac-125">By default, **EnableClientPrinting** is set to `true`.</span></span> <span data-ttu-id="522ac-126">다음과 같은 방법으로 클라이언트 쪽 인쇄 기능을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-126">You can disable client-side printing in the following ways:</span></span>  
  
-   <span data-ttu-id="522ac-127">**기본 모드 보고서 서버**:</span><span class="sxs-lookup"><span data-stu-id="522ac-127">For a **Native mode report server**:</span></span>  
  
    1.  <span data-ttu-id="522ac-128">관리자 권한으로 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-128">Start [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] with administrative privileges.</span></span>  
  
    2.  <span data-ttu-id="522ac-129">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 보고서 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-129">Connect to a report server instance in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
    3.  <span data-ttu-id="522ac-130">보고서 서버 노드를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-130">Right-click the report server node, and then click **Properties**.</span></span> <span data-ttu-id="522ac-131">**속성** 옵션이 해제되어 있으면 관리자 권한으로 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 를 실행했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-131">If the **Properties** option is disabled, verify you started [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] with administrative privileges.</span></span>  
  
    4.  <span data-ttu-id="522ac-132">**ActiveX 클라이언트 인쇄 컨트롤에 대해 다운로드 사용을**선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-132">Select **Enable download for the ActiveX client print control**.</span></span>  
  
    5.  <span data-ttu-id="522ac-133">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-133">Click **OK**.</span></span>  
  
-   <span data-ttu-id="522ac-134">**SharePoint 모드 보고서 서버**:</span><span class="sxs-lookup"><span data-stu-id="522ac-134">For a **SharePoint mode report server**:</span></span>  
  
    1.  <span data-ttu-id="522ac-135">SharePoint 중앙 관리에서 **애플리케이션 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-135">In SharePoint Central Administration, click **Application Management**.</span></span>  
  
    2.  <span data-ttu-id="522ac-136">**서비스 애플리케이션 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-136">Click **Manage service applications**.</span></span>  
  
    3.  <span data-ttu-id="522ac-137">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션의 이름을 클릭하고 SharePoint 리본 메뉴에서 **관리** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-137">Click the name of your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application, and then click **Manage** in the SharePoint ribbon.</span></span>  
  
    4.  <span data-ttu-id="522ac-138">**시스템 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-138">Click **System Settings**.</span></span>  
  
    5.  <span data-ttu-id="522ac-139">**클라이언트 인쇄 사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-139">Select **Enable Client Printing**.</span></span> <span data-ttu-id="522ac-140">**클라이언트 인쇄 사용** 옵션은 페이지 아래쪽에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-140">The **Enable Client Printing** option is near the bottom of the page.</span></span>  
  
    6.  <span data-ttu-id="522ac-141">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-141">Click **OK**.</span></span>  
  
-   <span data-ttu-id="522ac-142">보고서 서버 시스템 속성 **EnableClientPrinting** 를 설정 하는 스크립트 또는 코드를 작성 합니다.`false.`</span><span class="sxs-lookup"><span data-stu-id="522ac-142">Write script or code to set the report server system property **EnableClientPrinting** to `false.`</span></span>  
  
 <span data-ttu-id="522ac-143">다음 예제 스크립트에서는 클라이언트 쪽 인쇄 기능을 해제하는 한 가지 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-143">The following sample script illustrates one approach for disabling client-side printing.</span></span> <span data-ttu-id="522ac-144">다음 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 코드를 컴파일한 후 실행하여 **EnableClientPrinting** 속성을 **False**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-144">Compile and then run the following [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] code to set the **EnableClientPrinting** property to **False**.</span></span> <span data-ttu-id="522ac-145">코드를 실행한 후에는 IIS를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="522ac-145">After you run the code, restart IIS.</span></span>  
  
### <a name="sample-script"></a><span data-ttu-id="522ac-146">예제 스크립트</span><span class="sxs-lookup"><span data-stu-id="522ac-146">Sample Script</span></span>  
  
```  
Imports System  
Imports System.Web.Services.Protocols  
Class Sample  
   Public Shared Sub Main()  
Dim rs As New ReportingService()  
      rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
        Dim props(0) As [Property]  
        Dim setProp As New [Property]  
        setProp.Name = "EnableClientPrinting"  
        setProp.Value = "False"   
        props(0) = setProp  
        Try  
            rs.SetSystemProperties(props)  
        Catch ex As System.Web.Services.Protocols.SoapException  
            Console.Write(ex.Detail.InnerXml)  
        Catch e as Exception  
            Console.Write(e.Message)  
        End Try  
    End Sub 'Main  
End Class 'Sample  
```  
  
  

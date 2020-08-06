---
title: 실행 계정 (SSRS 기본 모드) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.executionaccount.F1
ms.assetid: 440b5a09-5fd4-4c3a-b510-f3c33cbf1c82
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 10e158eb38b9d1f94257f48339bb63bae2d3b61b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653184"
---
# <a name="execution-account-ssrs-native-mode"></a><span data-ttu-id="39799-102">실행 계정(SSRS 기본 모드)</span><span class="sxs-lookup"><span data-stu-id="39799-102">Execution Account (SSRS Native Mode)</span></span>
  <span data-ttu-id="39799-103">이 페이지를 사용하여 무인 모드 처리용으로 사용할 계정을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39799-103">Use this page to configure an account to use for unattended processing.</span></span> <span data-ttu-id="39799-104">이 계정은 다음과 같이 다른 자격 증명 원본을 사용할 수 없는 특별한 환경에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="39799-104">This account is used under special circumstances when other sources of credentials are not available:</span></span>  
  
-   <span data-ttu-id="39799-105">보고서 서버가 자격 증명이 필요 없는 데이터 원본에 연결하는 경우</span><span class="sxs-lookup"><span data-stu-id="39799-105">When the report server connects to a data source that does not require credentials.</span></span> <span data-ttu-id="39799-106">자격 증명이 필요 없는 데이터 원본의 예로는 XML 문서와 일부 클라이언트 쪽 애플리케이션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39799-106">Examples of data sources that might not require credentials include XML documents and some client-side database applications.</span></span>  
  
-   <span data-ttu-id="39799-107">보고서 서버가 보고서에서 참조하는 외부 이미지 파일 또는 기타 리소스를 검색하기 위해 다른 서버에 연결하는 경우</span><span class="sxs-lookup"><span data-stu-id="39799-107">When the report server connects to another server to retrieve external image files or other resources that are referenced in a report.</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="39799-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]기본 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="39799-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
 <span data-ttu-id="39799-109">이 계정 설정은 선택 사항이지만 설정하지 않은 경우 외부 이미지 및 일부 데이터 원본에 대한 연결을 사용하는 데 제한이 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="39799-109">Setting this account is optional, but not setting it limits your use of external images and connections to some data sources.</span></span> <span data-ttu-id="39799-110">외부 이미지 파일을 검색할 때 보고서 서버는 익명 연결을 설정할 수 있는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="39799-110">When retrieving external image files, the report server checks to see if an anonymous connection can be made.</span></span> <span data-ttu-id="39799-111">연결이 암호로 보호된 경우 보고서 서버는 무인 보고서 처리 계정을 사용하여 원격 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="39799-111">If the connection is password protected, the report server uses the unattended report processing account to connect to the remote server.</span></span> <span data-ttu-id="39799-112">보고서에 대한 데이터를 검색할 때 데이터 원본 연결이 자격 증명 유형을 **없음** 으로 지정한 경우 보고서 서버는 현재 사용자를 가장하거나, 사용자에게 자격 증명을 요청하거나, 저장된 자격 증명을 사용하거나, 무인 처리 계정을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39799-112">When retrieving data for a report, the report server either impersonates the current user, prompts the user to provide credentials, uses stored credentials, or uses the unattended processing account if the data source connection specifies **None** as the credential type.</span></span> <span data-ttu-id="39799-113">보고서 서버는 다른 컴퓨터에 연결할 때 해당 서비스 계정 자격 증명을 위임 또는 가장할 수 없으므로 사용 가능한 다른 자격 증명이 없는 경우 무인 처리 계정을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39799-113">The report server does not allow its service account credentials to be delegated or impersonated when connecting to other computers, so it must use the unattended processing account if no other credentials are available.</span></span>  
  
 <span data-ttu-id="39799-114">서비스 계정을 실행하는 데 사용되는 계정과 다른 계정을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39799-114">The account you specify should be different from the one used to run the service account.</span></span> <span data-ttu-id="39799-115">이 계정을 구성할 경우 해당 계정은 RSReportServer.config 파일에 암호화된 값으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="39799-115">If you configure this account, it is stored in the RSReportServer.config file as an encrypted value.</span></span> <span data-ttu-id="39799-116">스케일 아웃 배포에서 보고서 서버를 실행하는 경우 이 계정은 각 보고서 서버에서 같은 방식으로 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39799-116">If you are running the report server in a scale-out deployment, you must configure this account the same way on each report server.</span></span>  
  
 <span data-ttu-id="39799-117">Windows 사용자 계정을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39799-117">You can use any Windows user account.</span></span> <span data-ttu-id="39799-118">최상의 결과를 얻으려면 다른 컴퓨터와의 연결을 지원하는 네트워크 로그온 권한과 읽기 권한을 가진 계정을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="39799-118">For best results, choose an account that has read permissions and network logon permissions to support connections to other computers.</span></span> <span data-ttu-id="39799-119">보고서에서 사용하려는 모든 외부 이미지 또는 데이터 파일에 대해 읽기 권한을 갖고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39799-119">It must have read permissions on any external image or data file that you want to use in a report.</span></span> <span data-ttu-id="39799-120">모든 보고서 데이터 원본과 외부 이미지가 보고서 서버 컴퓨터에 저장되어 있지 않으면 로컬 계정을 지정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="39799-120">Do not specify a local account unless all report data sources and external images are stored on the report server computer.</span></span> <span data-ttu-id="39799-121">이 계정은 무인 보고서 처리에만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39799-121">Use the account only for unattended report processing.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="39799-122">[!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)] 을 사용하는 경우 보고서에서 외부 이미지를 참조하고 해당 이미지 파일에 액세스하는 데 사용 권한이 필요할 때만 이 계정을 구성하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39799-122">If you are using [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)] with Advanced Services, you only need to configure this account if you are referencing external images in a report and permission is required to access the image file.</span></span> <span data-ttu-id="39799-123">SQL Server Express는 원격 서버에 대한 데이터 원본 연결을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="39799-123">SQL Server Express does not support a data source connection to a remote server.</span></span> <span data-ttu-id="39799-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전에서 지원되는 기능 목록은 [SQL Server 2012 버전에서 지원하는 기능](https://go.microsoft.com/fwlink/?linkid=232473)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39799-124">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473).</span></span>  
  
 <span data-ttu-id="39799-125">이 페이지를 열려면 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자를 시작하고 탐색 창에서 **실행 계정** 에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="39799-125">To open this page, start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager and select **Execution Account** in the navigation pane.</span></span> <span data-ttu-id="39799-126">자세한 내용은 [Reporting Services 구성 관리자&#40;기본 모드&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39799-126">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="39799-127">옵션</span><span class="sxs-lookup"><span data-stu-id="39799-127">Options</span></span>  
 <span data-ttu-id="39799-128">**실행 계정 지정**</span><span class="sxs-lookup"><span data-stu-id="39799-128">**Specify an execution account**</span></span>  
 <span data-ttu-id="39799-129">계정을 지정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="39799-129">Select to specify an account.</span></span>  
  
 <span data-ttu-id="39799-130">**계정**</span><span class="sxs-lookup"><span data-stu-id="39799-130">**Account**</span></span>  
 <span data-ttu-id="39799-131">Windows 도메인 사용자 계정을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="39799-131">Enter a Windows domain user account.</span></span> <span data-ttu-id="39799-132">\* \<domain> \\ 사용자 계정 \><\* 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="39799-132">Use this format: *\<domain>\\<user account\>*.</span></span>  
  
 <span data-ttu-id="39799-133">**암호**</span><span class="sxs-lookup"><span data-stu-id="39799-133">**Password**</span></span>  
 <span data-ttu-id="39799-134">암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="39799-134">Type the password.</span></span>  
  
 <span data-ttu-id="39799-135">**암호 확인**</span><span class="sxs-lookup"><span data-stu-id="39799-135">**Confirm password**</span></span>  
 <span data-ttu-id="39799-136">암호를 다시 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="39799-136">Retype the password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39799-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="39799-137">See Also</span></span>  
 <span data-ttu-id="39799-138">[Reporting Services 구성 관리자 F1 도움말 항목 &#40;SSRS 기본 모드&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="39799-138">[Reporting Services Configuration Manager F1 Help Topics &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="39799-139">[암호화된 보고서 서버 데이터 저장&#40;SSRS 구성 관리자&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span><span class="sxs-lookup"><span data-stu-id="39799-139">[Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span></span>  
 [<span data-ttu-id="39799-140">무인 실행 계정 구성&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="39799-140">Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;</span></span>](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)  
  
  

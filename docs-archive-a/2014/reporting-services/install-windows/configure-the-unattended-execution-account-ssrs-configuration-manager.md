---
title: 무인 실행 계정 구성(SSRS 구성 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- no credentials option [Reporting Services]
- security [Reporting Services], unattended report processing
- unattended report processing [Reporting Services]
- credentials [Reporting Services]
- external data sources [Reporting Services]
- accounts [Reporting Services]
- reports [Reporting Services], processing
ms.assetid: 4e50733e-bd8c-4bf6-8379-98b1531bb9ca
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 437b28b57bc304d079acea3123983bed389341ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732443"
---
# <a name="configure-the-unattended-execution-account-ssrs-configuration-manager"></a><span data-ttu-id="20101-102">무인 실행 계정 구성(SSRS 구성 관리자)</span><span class="sxs-lookup"><span data-stu-id="20101-102">Configure the Unattended Execution Account (SSRS Configuration Manager)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="20101-103">에서는 무인 모드로 보고서를 처리하고 네트워크를 통해 연결 요청을 전송하는 데 사용되는 특수 계정을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-103">provides a special account that is used for unattended report processing and for sending connection requests across the network.</span></span> <span data-ttu-id="20101-104">이 계정은 다음과 같은 방법으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="20101-104">The account is used in the following ways:</span></span>  
  
-   <span data-ttu-id="20101-105">데이터베이스 인증을 사용하는 보고서에 대해 네트워크로 연결 요청을 전송하거나 인증을 요구 또는 사용하지 않는 외부 보고서 데이터 원본에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-105">Send connection requests over the network for reports that use database authentication, or connect to external report data sources that do not require or use authentication.</span></span> <span data-ttu-id="20101-106">자세한 내용은 SQL Server 온라인 설명서에서 [보고서 데이터 원본에 대한 자격 증명 및 연결 정보 지정](../../integration-services/connection-manager/data-sources.md) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="20101-106">For more information, see [Specify Credential and Connection Information for Report Data Sources](../../integration-services/connection-manager/data-sources.md) in SQL Server Books Online.</span></span>  
  
-   <span data-ttu-id="20101-107">보고서에 사용되는 외부 이미지 파일 검색.</span><span class="sxs-lookup"><span data-stu-id="20101-107">Retrieve external image files that are used in report.</span></span> <span data-ttu-id="20101-108">이미지 파일을 사용하려는 경우 익명 액세스를 통해 해당 파일에 액세스할 수 없으면 무인 모드로 실행되는 보고서 처리 계정을 구성하고 이 계정에 해당 파일에 액세스할 수 있는 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20101-108">If you want to use an image file and the file cannot be accessed through Anonymous access, you can configure the unattended report processing account and grant the account permission to access the file.</span></span>  
  
 <span data-ttu-id="20101-109">무인 모드로 실행되는 보고서 처리란 사용자 요청 대신 이벤트(일정 기반 이벤트 또는 데이터 새로 고침 이벤트)에 의해 트리거되는 모든 보고서 실행 프로세스를 말합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-109">Unattended report processing refers to any report execution process that is triggered by an event (either a schedule-driven event or data refresh event) rather than a user request.</span></span> <span data-ttu-id="20101-110">보고서 서버는 무인 모드로 실행되는 보고서 처리 계정을 사용하여 외부 데이터 원본을 호스팅하는 컴퓨터에 로그온합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-110">The report server uses the unattended report processing account to log on to the computer that hosts the external data source.</span></span> <span data-ttu-id="20101-111">보고서 서버 서비스 계정의 자격 증명은 다른 컴퓨터에 연결할 때 사용되지 않으므로 이 계정이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-111">This account is necessary because the credentials of the Report Server service account are never used to connect to other computers.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="20101-112">이 계정 구성은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="20101-112">Configuring the account is optional.</span></span> <span data-ttu-id="20101-113">그러나 계정을 구성하지 않는 경우 일부 데이터 원본에 연결하는 옵션이 제한되며 원격 컴퓨터에서 이미지 파일을 검색하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20101-113">However, if you do not configure it, you will limit your options for connecting to some data sources, and you might not be able to retrieve image files from remote computers.</span></span> <span data-ttu-id="20101-114">계정을 구성하는 경우 최신 상태로 유지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-114">If you do configure the account, you must keep it up to date.</span></span> <span data-ttu-id="20101-115">특히 암호가 만료되도록 하거나 Active Directory에서 계정 정보를 변경하는 경우 다음에 보고서를 처리하면 "로그온하지 못했습니다(rsLogonFailed). 로그온 실패: 알 수 없는 사용자 이름이거나 암호가 틀립니다."와 같은 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20101-115">Specifically, if you allow a password to expire or the account information is changed in Active Directory, you will encounter the following error the next time a report is processed: "Logon failed (rsLogonFailed) Logon failure: unknown user name or bad password."</span></span> <span data-ttu-id="20101-116">외부 이미지를 검색하거나 연결 요청을 외부 컴퓨터로 보내지 않는 경우에도 무인 모드로 실행되는 보고서 처리 계정을 적절하게 유지 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-116">Proper maintenance of the unattended report processing account is essential, even if you never retrieve external images or send connection requests to external computers.</span></span> <span data-ttu-id="20101-117">계정을 구성한 다음 사용할 필요가 없게 되면 삭제하여 일상적인 계정 유지 관리 태스크를 수행하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20101-117">If you configure the account but then find that you are not using it, you can delete it to avoid routine account maintenance tasks.</span></span>  
  
## <a name="how-to-configure-the-account"></a><span data-ttu-id="20101-118">계정 구성 방법</span><span class="sxs-lookup"><span data-stu-id="20101-118">How to Configure the Account</span></span>  
 <span data-ttu-id="20101-119">도메인 사용자 계정을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-119">You must use a domain user account.</span></span> <span data-ttu-id="20101-120">원래 용도대로 사용하려면 이 계정은 보고서 서버 서비스를 실행하는 데 사용되는 계정과 달라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-120">To serve its intended purpose, this account should be different than the one used to run the Report Server service.</span></span> <span data-ttu-id="20101-121">보고서 서버에 데이터 원본 및 리소스를 제공하는 컴퓨터에 대해서만 최소 사용 권한(네트워크 연결 권한이 포함된 읽기 전용 액세스 권한이면 충분함)과 제한된 액세스 권한이 있는 계정을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-121">Be sure to use an account that has minimum permissions (read-only access with network connection permissions is sufficient) and limited access to just those computers that provide data sources and resources to the report server.</span></span> <span data-ttu-id="20101-122">자세한 내용은 [Reporting Services 구성 관리자&#40;기본 모드&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="20101-122">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
 <span data-ttu-id="20101-123">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구 또는 **rsconfig** 유틸리티를 사용하여 계정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20101-123">To specify the account, you can use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool or the **rsconfig** utility.</span></span> <span data-ttu-id="20101-124">무인 실행 계정을 구성하는 가장 쉬운 방법은 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구를 실행하여 실행 계정 페이지에서 자격 증명을 지정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="20101-124">The easiest way to configure the unattended execution account is to run the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and specify credentials in the Execution Account page.</span></span>  
  
1.  <span data-ttu-id="20101-125">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구를 시작한 후 구성하려는 보고서 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-125">Start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and connect to the report server instance you want to configure.</span></span> <span data-ttu-id="20101-126">자세한 내용은 [Reporting Services 구성 관리자&#40;기본 모드&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="20101-126">For instructions, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="20101-127">실행 계정 페이지에서 **실행 계정 지정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-127">On the Execution Account page, select **Specify an execution account**.</span></span>  
  
3.  <span data-ttu-id="20101-128">계정 및 암호를 입력하고 암호를 다시 입력한 다음 **적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-128">Type the account and password, retype the password, and then click **Apply**.</span></span>  
  
### <a name="using-rsconfig-utility"></a><span data-ttu-id="20101-129">RSCONFIG 유틸리티 사용</span><span class="sxs-lookup"><span data-stu-id="20101-129">Using RSCONFIG Utility</span></span>  
 <span data-ttu-id="20101-130">계정을 설정하는 다른 방법은 **rsconfig** 유틸리티를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="20101-130">Another way to set the account is to use the **rsconfig** utility.</span></span> <span data-ttu-id="20101-131">계정을 지정하려면 **rsconfig** 의 **-e**인수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-131">To specify the account, use the **-e** argument of **rsconfig**.</span></span> <span data-ttu-id="20101-132">**rsconfig** 에 **-e** 인수를 지정하면 유틸리티가 계정 정보를 구성 파일에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-132">Specifying the **-e** argument for **rsconfig** directs the utility to write the account information to the configuration file.</span></span> <span data-ttu-id="20101-133">RSreportserver.config에 대한 경로를 지정할 필요는 없습니다. 다음 단계에 따라 계정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-133">You do not need to specify a path to RSreportserver.config. Follow these steps to configure the account.</span></span>  
  
1.  <span data-ttu-id="20101-134">보고서 서버에 데이터 또는 서비스를 제공하는 컴퓨터와 서버에 액세스할 수 있는 도메인 계정을 만들거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-134">Create or select a domain account that has access to computers and servers that provide data or services to a report server.</span></span> <span data-ttu-id="20101-135">축소된 권한(예: 읽기 전용 권한)을 가진 계정을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-135">You should use an account that has reduced permissions (for example, read-only permissions).</span></span>  
  
2.  <span data-ttu-id="20101-136">명령 프롬프트 열기: **시작** 메뉴에서 **실행**을 클릭한 다음 **cmd**를 입력하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-136">Open a command prompt: On the **Start** menu, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="20101-137">다음 명령을 입력하여 로컬 보고서 서버 인스턴스에서 계정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-137">Type the following command to configure the account on a local report server instance:</span></span>  
  
     <span data-ttu-id="20101-138">**rsconfig-e-u- \<domain/username> p\<password>**</span><span class="sxs-lookup"><span data-stu-id="20101-138">**rsconfig -e -u\<domain/username> -p\<password>**</span></span>  
  
 <span data-ttu-id="20101-139">**rsconfig -e** 는 추가 인수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-139">**rsconfig -e** supports additional arguments.</span></span> <span data-ttu-id="20101-140">구문에 대한 자세한 내용 및 명령 예제를 보려면 SQL Server 온라인 설명서에서 [rsconfig 유틸리티&#40;SSRS&#41;](../tools/rsconfig-utility-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="20101-140">For more information about syntax and to view command examples, see [rsconfig Utility &#40;SSRS&#41;](../tools/rsconfig-utility-ssrs.md) in SQL Server Books Online.</span></span>  
  
### <a name="how-account-information-is-stored"></a><span data-ttu-id="20101-141">계정 정보를 저장하는 방법</span><span class="sxs-lookup"><span data-stu-id="20101-141">How Account Information is Stored</span></span>  
 <span data-ttu-id="20101-142">계정을 설정하면 로컬 또는 원격 보고서 서버 인스턴스의 RSreportserver.config 파일에 다음 설정이 암호화된 값으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="20101-142">When you set the account, the following settings are specified as encrypted values in the RSreportserver.config file on a local or remote report server instance:</span></span>  
  
```  
<UnattendedExecutionAccount>  
     <UserName></UserName>  
     <Password></Password>  
     <Domain></Domain>  
</UnattendedExecutionAccount>  
```  
  
 <span data-ttu-id="20101-143">값을 설정한 후에는 암호를 해독하여 값을 일반 텍스트로 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="20101-143">Once you set the values, you cannot decrypt them to view the values in plain text.</span></span> <span data-ttu-id="20101-144">값을 잘못 입력했거나 지정한 값이 기억나지 않는 경우 Reporting Services 구성 도구를 사용하거나 **rsconfig -e** 를 실행하여 처음부터 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-144">If you mistype the values or forget the values you specified, you must use the Reporting Services Configuration tool or run **rsconfig -e** to start over.</span></span>  
  
## <a name="how-to-use-the-unattended-report-processing-account"></a><span data-ttu-id="20101-145">무인 보고서 처리 계정을 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="20101-145">How to Use the Unattended Report Processing Account</span></span>  
 <span data-ttu-id="20101-146">보고서 서버는 자동으로 계정을 사용하여 이미지 파일을 검색하므로 사용자가 별도의 동작을 수행하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="20101-146">To retrieve image files, the report server uses the account automatically and no specific action is required on your part.</span></span> <span data-ttu-id="20101-147">보고서에 데이터를 제공하는 외부 데이터 원본에 연결하는 데 계정을 사용하려면 보고서 데이터 원본 또는 공유 데이터 원본의 데이터 원본 속성 페이지에서 **자격 증명 유형** 옵션을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-147">To use the account to connect to external data sources that provide data to reports, you must specify a **Credential Type** option in the data source properties page of the report data source or shared data source:</span></span>  
  
-   <span data-ttu-id="20101-148">보고서 관리자 또는 SharePoint 사이트에서 **자격 증명 필요 없음** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-148">In Report Manager or on a SharePoint site, select the **Credentials are not required** option.</span></span>  
  
 <span data-ttu-id="20101-149">무인 보고서 처리 계정은 기본적으로 데이터베이스 서버에 로그인할 때가 아닌 외부 서버에 연결할 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="20101-149">The unattended report processing account is used primarily to connect to external servers, and not as a login to database servers.</span></span> <span data-ttu-id="20101-150">이 계정 자격 증명을 사용하여 데이터베이스에 로그인하려면 연결 문자열에 자격 증명을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-150">If you want to use the account credentials to log in to a database, you must specify credentials in the connection string.</span></span> <span data-ttu-id="20101-151">데이터베이스 서버가 Windows 통합 보안을 지원하고 무인 보고서 처리에 사용된 계정에 데이터베이스 읽기 권한이 있는 경우 **Integrated Security=SSPI** 를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20101-151">You can specify **Integrated Security=SSPI** if the database server supports Windows integrated security and the account used for unattended report processing has permission to read the database.</span></span> <span data-ttu-id="20101-152">그렇지 않은 경우, 연결 문자열에 사용자 이름 및 암호를 입력해야 하며 이것은 데이터 원본 연결 속성에 대한 편집 권한이 있는 모든 사용자에게 일반 텍스트로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="20101-152">Otherwise, you must enter the user name and password in the connection string, where it appears in clear text to any user who has permission to edit data source connection properties.</span></span>  
  
 <span data-ttu-id="20101-153">연결을 설정한 후에 무인 보고서 처리 계정을 사용하여 데이터를 검색할 수 있지만 이 방법은 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="20101-153">Although you are not prevented from using the unattended report processing account to retrieve data after the connection is made, doing so is not recommended.</span></span> <span data-ttu-id="20101-154">이 계정은 아주 특별한 기능을 위해 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-154">The account is supposed to be used for very specific functions.</span></span> <span data-ttu-id="20101-155">데이터 검색에 이 계정을 사용하면 본래의 용도가 훼손될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20101-155">If you use it to retrieve data, you undermine the purpose for which it is intended.</span></span>  
  
## <a name="how-to-maintain-the-unattended-report-processing-account"></a><span data-ttu-id="20101-156">무인 보고서 처리 계정을 유지 관리하는 방법</span><span class="sxs-lookup"><span data-stu-id="20101-156">How to Maintain the Unattended Report Processing Account</span></span>  
 <span data-ttu-id="20101-157">계정을 정의한 다음에는 계정과 암호를 최신 상태로 유지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-157">Once you define the account, you must ensure that the account and password are kept up to date.</span></span> <span data-ttu-id="20101-158">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구를 사용하여 이 계정에 대한 정보가 저장된 구성 설정을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20101-158">You can use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool to update the configuration settings that store information about this account.</span></span>  
  
1.  <span data-ttu-id="20101-159">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구를 시작한 후 구성하려는 보고서 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-159">Start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and connect to the report server instance you want to configure.</span></span>  
  
2.  <span data-ttu-id="20101-160">실행 계정 페이지에서 **실행 계정 지정** 이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-160">On the Execution Account page, verify that **Specify an execution account** is selected.</span></span>  
  
3.  <span data-ttu-id="20101-161">새 계정 및 암호를 입력하고 암호를 다시 입력한 다음 **적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-161">Type the new account or password, retype the password, and then click **Apply**.</span></span>  
  
## <a name="how-to-delete-the-unattended-report-processing-account"></a><span data-ttu-id="20101-162">무인 보고서 처리 계정을 삭제하는 방법</span><span class="sxs-lookup"><span data-stu-id="20101-162">How to Delete the Unattended Report Processing Account</span></span>  
 <span data-ttu-id="20101-163">계정을 사용할 필요가 없게 되면 삭제하여 일상적인 계정 유지 관리 태스크를 수행하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20101-163">If you are not using the account, you can delete it to avoid routine account maintenance tasks.</span></span>  
  
1.  <span data-ttu-id="20101-164">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구를 시작한 후 구성하려는 보고서 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-164">Start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and connect to the report server instance you want to configure.</span></span>  
  
2.  <span data-ttu-id="20101-165">실행 계정 페이지에서 **실행 계정 지정**의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-165">On the Execution Account page, clear **Specify an execution account**.</span></span>  
  
3.  <span data-ttu-id="20101-166">**적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="20101-166">Click **Apply**.</span></span>  
  
 <span data-ttu-id="20101-167">계정 정보가 RSReportServer.config 파일에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="20101-167">The account information is removed from the RSReportServer.config file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20101-168">참고 항목</span><span class="sxs-lookup"><span data-stu-id="20101-168">See Also</span></span>  
 [<span data-ttu-id="20101-169">Reporting Services 구성 관리자 &#40;del&#41;</span><span class="sxs-lookup"><span data-stu-id="20101-169">Reporting Services Configuration Manager &#40;del&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  

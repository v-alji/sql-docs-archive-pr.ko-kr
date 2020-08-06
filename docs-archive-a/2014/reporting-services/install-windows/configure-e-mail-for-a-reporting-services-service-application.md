---
title: Reporting Services 서비스 응용 프로그램에 대 한 전자 메일 구성 (SharePoint 2010 및 SharePoint 2013) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 38fc34a6-aae7-4dde-9ad2-f1eee0c42a9f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 628122289f8a9d83a307d70a369ab51f8f571c04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652628"
---
# <a name="configure-e-mail-for-a-reporting-services-service-application-sharepoint-2010-and-sharepoint-2013"></a><span data-ttu-id="b7b83-102">Reporting Services 서비스 애플리케이션(SharePoint 2010 및 SharePoint 2013)에 대한 전자 메일 구성</span><span class="sxs-lookup"><span data-stu-id="b7b83-102">Configure E-mail for a Reporting Services Service Application (SharePoint 2010 and SharePoint 2013)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="b7b83-103">데이터 경고는 메일 메시지로 경고를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="b7b83-103">data alerting sends alerts in e-mail messages.</span></span> <span data-ttu-id="b7b83-104">전자 메일을 보내기 위해 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션을 구성하고 서비스 애플리케이션을 위한 전자 메일 배달 확장 프로그램을 수정해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7b83-104">To send e-mail you may need to configure your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application and you may need to modify the e-mail delivery extension for the service application.</span></span> <span data-ttu-id="b7b83-105">또한 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 가입 기능을 위해 전자 메일 배달 확장 프로그램을 사용할 계획인 경우에도 전자 메일 설정이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b83-105">The e-mail settings are also required if you plan to use the e-mail delivery extension for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscription feature.</span></span>  
  
||  
|-|  
|[!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="b7b83-106">Sharepoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 모드 &#124; sharepoint 2010 및 sharepoint 2013입니다.</span><span class="sxs-lookup"><span data-stu-id="b7b83-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode &#124; SharePoint 2010 and SharePoint 2013.</span></span>|  
  
### <a name="to-configure-e-mail-for-the-shared-service"></a><span data-ttu-id="b7b83-107">공유 서비스에 대한 전자 메일 구성 방법</span><span class="sxs-lookup"><span data-stu-id="b7b83-107">To configure e-mail for the shared service</span></span>  
  
1.  <span data-ttu-id="b7b83-108">SharePoint 중앙 관리에서 **애플리케이션 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b83-108">In SharePoint Central Administration, click the **Application Management**.</span></span>  
  
2.  <span data-ttu-id="b7b83-109">**서비스 애플리케이션** 그룹에서 **서비스 애플리케이션 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b83-109">In the **Service Applications** group, click **Manage service applications**.</span></span>  
  
3.  <span data-ttu-id="b7b83-110">**이름** 목록에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션의 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b83-110">In the **Name** list, click the name of your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
4.  <span data-ttu-id="b7b83-111">**Reporting Services 애플리케이션 관리** 페이지에서 **메일 설정** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b83-111">Click **E-mail Settings** on the **Manage Reporting Services Application** page.</span></span>  
  
5.  <span data-ttu-id="b7b83-112">**SMTP 서버 사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b83-112">Select **Use SMTP server**.</span></span>  
  
6.  <span data-ttu-id="b7b83-113">**아웃바운드 SMTP 서버** 상자에 SMTP 서버 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b83-113">In the **Outbound SMTP server** box, type the name of an SMTP server.</span></span>  
  
7.  <span data-ttu-id="b7b83-114">**보낸 사람 주소** 상자에서 메일 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b83-114">In the **From address** box, type an e-mail address.</span></span>  
  
     <span data-ttu-id="b7b83-115">이 주소는 모든 경고 전자 메일 메시지의 받는 사람입니다.</span><span class="sxs-lookup"><span data-stu-id="b7b83-115">This address is the sender of all alert e-mail messages.</span></span>  
  
     <span data-ttu-id="b7b83-116">**보낸 사람 주소** 에 지정한 사용자 계정은 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션의 애플리케이션 풀을 구성할 때 지정한 관리 계정이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b83-116">The account of the user specified in **From address** must be a managed account that you specified when you configured the application pool for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="b7b83-117">권한이 있는 경우 SharePoint 중앙 관리의 서비스 계정 페이지에서 기존 관리 계정 목록을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7b83-117">If you have permission, you can view a list of existing managed accounts on the Service Accounts page in SharePoint Central Administration.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="ntlm-authentication"></a><span data-ttu-id="b7b83-118">NTLM 인증</span><span class="sxs-lookup"><span data-stu-id="b7b83-118">NTLM Authentication</span></span>  
  
1.  <span data-ttu-id="b7b83-119">해당 전자 메일 환경에서 NTLM 인증이 필요하고 익명 액세스가 허용되지 않는 경우 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션에 대해 전자 메일 배달 확장 프로그램 구성을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b83-119">If your email environment requires NTLM authentication and does not allow anonymous access, you need to modify the e-mail delivery extension configuration for your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications.</span></span> <span data-ttu-id="b7b83-120">값 "2"를 사용 하도록 **SMTPAuthenticate** 를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b83-120">Change the **SMTPAuthenticate** to use a value of "2".</span></span> <span data-ttu-id="b7b83-121">이 값은 사용자 인터페이스에서 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b7b83-121">This value cannot be changed from the user interface.</span></span> <span data-ttu-id="b7b83-122">다음 PowerShell 스크립트 예에서 "SSRS_TESTAPPLICATION" 서비스 애플리케이션에 대해 보고서 서버 이메일 배달 확장 프로그램의 전체 구성을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b83-122">The following PowerShell script example, updates the full configuration for the report server e-mail delivery extension for the service application named "SSRS_TESTAPPLICATION".</span></span> <span data-ttu-id="b7b83-123">또한 예를 들어 "보낸 사람" 주소와 같이 스크립트에 나열된 일부 노드는 사용자 인터페이스에서 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7b83-123">Note some of the nodes listed in the script can also be set from the user interface, for example the "From" address.</span></span>  
  
    ```powershell
    $app = Get-SPRSServiceApplication | Where {$_.name -like "SSRS_TESTAPPLICATION *"}  
    $emailCfg = Get-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml
    $emailXml = [xml]$emailCfg
    $emailXml.SelectSingleNode("//SMTPServer").InnerText = "your email server name"  
    $emailXml.SelectSingleNode("//SendUsing").InnerText = "2"  
    $emailXml.SelectSingleNode("//SMTPAuthenticate").InnerText = "2"  
    $emailXml.SelectSingleNode("//From").InnerText = "your FROM email address"  
    Set-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" -ExtensionConfiguration $emailXml.OuterXml  
    ```  
  
2.  <span data-ttu-id="b7b83-124">서비스 응용 프로그램의 이름을 확인 해야 하는 경우 **get-sprsserviceapplication** cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b83-124">If you need to verify the name of your service application, run the **Get-SPRSServiceApplication** cmdlet.</span></span>  
  
    ```powershell
    Get-SPRSServiceApplication  
    ```  
  
3.  <span data-ttu-id="b7b83-125">다음 예제에서 "SSRS_TESTAPPLICATION" 서비스 애플리케이션에 대해 이메일 확장 프로그램의 현재 값으로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="b7b83-125">The following example will return the current values of the e-mail extension for the service application named "SSRS_TESTAPPLICATION".</span></span>  
  
    ```powershell
    $app = get-sprsserviceapplication | Where {$_.name -like "SSRSTEST_APPLICATION*"}  
    Get-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml  
    ```  
  
4.  <span data-ttu-id="b7b83-126">다음 예제에서 "SSRS_TESTAPPLICATION" 서비스 애플리케이션에 대해 이메일 확장 프로그램의 현재 값을 가진 "emailconfig.txt"라는 새 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b7b83-126">The following example will create a new file named "emailconfig.txt" with the current values of the e-mail extension for the service application named "SSRS_TESTAPPLICATION"</span></span>  
  
    ```powershell
    $app = Get-SPRSServiceApplication | Where {$_.name -like "SSRS_TESTAPPLICATION*"}  
    Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | Select -ExpandProperty ConfigurationXml | Out-File c:\emailconfig.txt  
    ```

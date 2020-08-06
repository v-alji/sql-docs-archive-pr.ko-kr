---
title: PowerPivot 데이터 새로 고침을 위한 저장 된 자격 증명 구성 (SharePoint용 PowerPivot) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 987eff0f-bcfe-4bbd-81e0-9aca993a2a75
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5a1350c5d776891397401e9d3127b7849281b106
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648034"
---
# <a name="configure-stored-credentials-for-powerpivot-data-refresh-powerpivot-for-sharepoint"></a><span data-ttu-id="3f4bc-102">PowerPivot 데이터 새로 고침을 위한 저장된 자격 증명 구성(SharePoint용 PowerPivot)</span><span class="sxs-lookup"><span data-stu-id="3f4bc-102">Configure Stored Credentials for PowerPivot Data Refresh (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="3f4bc-103">사용하려는 자격 증명을 저장할 대상 애플리케이션을 Secure Store Service에 만들면 Windows 사용자 계정으로 PowerPivot 데이터 새로 고침 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-103">PowerPivot data refresh jobs can run under any Windows user account as long as you create a target application in Secure Store Service to store the credentials you want to use.</span></span> <span data-ttu-id="3f4bc-104">마찬가지로, 원래 PowerPivot for Excel에서 데이터를 가져오는 데 사용된 것과 다른 데이터베이스 로그인을 제공하려는 경우 해당 자격 증명을 보안 스토리지 서비스 대상 애플리케이션에 매핑한 다음 데이터 새로 고침 일정에서 해당 애플리케이션을 지정하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-104">Similarly, if you want to provide a database login that varies from the one used to originally import the data in PowerPivot for Excel, you can map those credentials to a Secure Store Service target application, and then specify that target application in a data refresh schedule.</span></span>  
  
 <span data-ttu-id="3f4bc-105">**[!INCLUDE[applies](../includes/applies-md.md)]** SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="3f4bc-105">**[!INCLUDE[applies](../includes/applies-md.md)]**  SharePoint 2010</span></span>  
  
 <span data-ttu-id="3f4bc-106">이 항목의 지침을 따른 후 PowerPivot 데이터 새로 고침 일정 페이지에서 다음과 같은 자격 증명 옵션을 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-106">After you follow the instructions in this topic, you will be able to use the following credentials option in the PowerPivot data refresh schedule page:</span></span>  
  
 <span data-ttu-id="3f4bc-107">![SSAS_PowerPivotDataRefreshCreds_Stored](media/ssas-powerpivotdatarefreshcreds-stored.gif "SSAS_PowerPivotDataRefreshCreds_Stored")</span><span class="sxs-lookup"><span data-stu-id="3f4bc-107">![SSAS_PowerPivotDataRefreshCreds_Stored](media/ssas-powerpivotdatarefreshcreds-stored.gif "SSAS_PowerPivotDataRefreshCreds_Stored")</span></span>  
  
 <span data-ttu-id="3f4bc-108">이 항목에서는 SharePoint 2010 팜에서 PowerPivot 데이터 새로 고침 작업에 사용되는 사용자 이름과 암호를 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-108">This topic explains how to set up the user names and passwords that are used for PowerPivot data refresh in a SharePoint 2010 farm.</span></span> <span data-ttu-id="3f4bc-109">이 단계를 수행하려면 Secure Store Service를 사용하도록 설정하고 마스터 키를 생성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-109">Before you can use these steps, you must have enabled Secure Store Service and generated a master key.</span></span> <span data-ttu-id="3f4bc-110">자세한 내용은 [SharePoint 2010를 사용 하 여 PowerPivot 데이터 새로 고침](powerpivot-data-refresh-with-sharepoint-2010.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-110">For more information, see [PowerPivot Data Refresh with SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md)</span></span>  
  
 <span data-ttu-id="3f4bc-111">이 항목에는 다음과 같은 섹션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-111">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="3f4bc-112">데이터 새로 고침에 대한 Windows 계정 구성</span><span class="sxs-lookup"><span data-stu-id="3f4bc-112">Configure any Windows account for data refresh</span></span>](#configAny)  
  
 [<span data-ttu-id="3f4bc-113">외부 또는 타사 데이터 원본에 액세스하기 위한 미리 정의된 계정 구성</span><span class="sxs-lookup"><span data-stu-id="3f4bc-113">Configure a predefined account for accessing external or third-party data sources</span></span>](#config3rd)  
  
 <span data-ttu-id="3f4bc-114">데이터 새로 고침을 구성 하거나 사용 하는 데 문제가 있는 경우 TechNet wiki의 [PowerPivot 데이터 새로 고침 문제 해결](https://go.microsoft.com/fwlink/?LinkID=223279) 페이지에서 가능한 해결 방법을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-114">If you have problems configuring or using data refresh, refer to the [Troubleshooting PowerPivot Data Refresh](https://go.microsoft.com/fwlink/?LinkID=223279) page on the TechNet wiki for possible solutions.</span></span>  
  
##  <a name="configure-any-windows-account-for-data-refresh"></a><a name="configAny"></a><span data-ttu-id="3f4bc-115">데이터 새로 고침을 위한 Windows 계정 구성</span><span class="sxs-lookup"><span data-stu-id="3f4bc-115">Configure any Windows account for data refresh</span></span>  
 <span data-ttu-id="3f4bc-116">SharePoint 사용자는 데이터 새로 고침 일정을 정의할 때 데이터 새로 고침이 수행될 사용자 ID를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-116">When a SharePoint user defines a data refresh schedule, he or she must specify the user identity under which data refresh is performed.</span></span> <span data-ttu-id="3f4bc-117">PowerPivot 무인 데이터 새로 고침 계정을 선택하거나 자신의 Windows 도메인 사용자 계정을 입력하거나 데이터 새로 고침 작업에 사용할 수 있는 다른 Windows 사용자 계정을 입력하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-117">Options include selecting the PowerPivot unattended data refresh account, entering his or her Windows domain user account, or entering some other Windows user account that is valid for data refresh purposes.</span></span> <span data-ttu-id="3f4bc-118">이 섹션의 단계에서는 다른 Windows 계정을 지정하는 마지막 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-118">The steps in this section are for the last option: specifying some other Windows account.</span></span>  
  
 <span data-ttu-id="3f4bc-119">이 방법은 PowerPivot 무인 데이터 새로 고침 계정(SharePoint의 모든 PowerPivot 사용자가 사용할 수 있는 계정) 또는 통합 문서 소유자의 자격 증명을 사용하는 것 외의 다른 옵션이 필요한 경우 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-119">You might choose this approach if you want an alternative to using the PowerPivot unattended data refresh account (available to all PowerPivot users on SharePoint) or the credentials of the workbook owner.</span></span> <span data-ttu-id="3f4bc-120">예를 들어 저마다 다른 작업 그룹에서 사용할 일련의 데이터 새로 고침 계정을 만들어 조직 수준에서 데이터 새로 고침 작업을 손쉽게 추적 및 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-120">For example, you might want to make a series of data refresh accounts available to different workgroups to help you track and manage data refresh activity at the organizational level.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3f4bc-121">이 대상 애플리케이션을 사용하는 사람과 대상 애플리케이션 및 대상 애플리케이션에 저장되는 자격 증명이 애플리케이션의 멤버로 나열되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-121">People and applications that use this target application (and the credentials that it stores) must be listed as members of the application.</span></span> <span data-ttu-id="3f4bc-122">대상 애플리케이션을 사용할 각 PowerPivot 서비스 애플리케이션의 ID, Windows 계정, 데이터 새로 고침 일정에서 이 대상 애플리케이션을 지정할 사용자 그룹 또는 사용자 계정을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-122">You must add the identity of each PowerPivot service application that will use the target application, your Windows account, and the group or user accounts of people who will be specifying this target application in their data refresh schedules.</span></span> <span data-ttu-id="3f4bc-123">대상 애플리케이션을 만들 때 이러한 계정을 모두 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-123">You can specify all of these accounts when you create the target application.</span></span> <span data-ttu-id="3f4bc-124">이 애플리케이션에 액세스해야 하는 일부 사용자 및 그룹 계정을 모를 경우 대상 애플리케이션을 만든 후 나중에 해당 사용자 및 그룹 계정을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-124">If you do not know all of the user and group accounts that will require access to this application, you can add them later after the target application is created.</span></span>  
  
 <span data-ttu-id="3f4bc-125">데이터 새로 고침에 대해 저장되는 자격 증명을 구성하려면 네 단계가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-125">There are 4 parts to configuring stored credentials for data refresh:</span></span>  
  
-   <span data-ttu-id="3f4bc-126">자격 증명을 저장하는 대상 애플리케이션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-126">Create the target application that stores the credentials.</span></span>  
  
-   <span data-ttu-id="3f4bc-127">계정에 참가 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-127">Grant Contribute permissions to the account.</span></span>  
  
-   <span data-ttu-id="3f4bc-128">데이터를 새로 고치는 동안 외부 데이터 원본에 액세스할 수 있는 읽기 권한을 이 계정에 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-128">Grant the account read permissions to access external data sources during data refresh.</span></span>  
  
-   <span data-ttu-id="3f4bc-129">데이터 새로 고침 일정에 이 대상 애플리케이션을 지정하면 데이터 새로 고침이 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-129">Verify that data refresh works when you specify this target application in a data refresh schedule.</span></span>  
  
### <a name="step-1-create-a-target-application"></a><span data-ttu-id="3f4bc-130">1 단계: 대상 응용 프로그램 만들기</span><span class="sxs-lookup"><span data-stu-id="3f4bc-130">Step 1: Create a target application</span></span>  
  
1.  <span data-ttu-id="3f4bc-131">중앙 관리의 애플리케이션 관리에서 **서비스 애플리케이션 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-131">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="3f4bc-132">**보안 저장소 서비스**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-132">Click **Secure Store Service**.</span></span>  
  
3.  <span data-ttu-id="3f4bc-133">대상 응용 프로그램 관리에서 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-133">In Manage Target Applications, click **New**.</span></span>  
  
4.  <span data-ttu-id="3f4bc-134">대상 애플리케이션 ID에 텍스트 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-134">In Target application ID, type a text string.</span></span> <span data-ttu-id="3f4bc-135">이 문자열은 고유하면서 기억하기도 쉬워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-135">The string must be unique, but it should also be easy to remember.</span></span> <span data-ttu-id="3f4bc-136">사용자는 이 애플리케이션에 저장된 자격 증명을 사용할 때마다 데이터 새로 고침 일정 페이지에서 이 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-136">Users will type this string in data refresh schedule pages whenever they want to use the credentials that are stored in this application.</span></span>  
  
5.  <span data-ttu-id="3f4bc-137">표시 이름에 응용 프로그램을 설명하는 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-137">In Display Name, enter a descriptive name.</span></span> <span data-ttu-id="3f4bc-138">이 이름은 표시용으로만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-138">This name is used for display purposes only.</span></span> <span data-ttu-id="3f4bc-139">이 이름은 데이터 새로 고침 일정에서 대상 애플리케이션을 지정하는 데 사용되는 이름이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-139">It is not used to specify the target application in a data refresh schedule.</span></span>  
  
6.  <span data-ttu-id="3f4bc-140">담당자 전자 메일에 사용자의 전자 메일 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-140">In Contact Email, type your e-mail address.</span></span>  
  
7.  <span data-ttu-id="3f4bc-141">대상 응용 프로그램 형식에서 **그룹**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-141">In Target Application Type, select **Group**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="3f4bc-142">그룹 계정 유형을 사용하면 자격 증명에 대한 액세스를 요청하는 모든 사용자 및 서비스 계정을 지정할 수 있으므로 그룹 계정 유형을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-142">Choosing a Group account type is necessary because it allows you to specify all of the user and service accounts requesting access to the credentials.</span></span> <span data-ttu-id="3f4bc-143">PowerPivot 시스템 서비스는 각 요청에 대해 요청자가 대상 애플리케이션의 멤버인지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-143">For each request, PowerPivot System Service verifies whether the requestor is a member of the target application.</span></span>  
  
8.  <span data-ttu-id="3f4bc-144">대상 애플리케이션 페이지 URL을 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-144">Skip Target Application Page URL.</span></span> <span data-ttu-id="3f4bc-145">PowerPivot 데이터 새로 고침에서 이 URL을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-145">PowerPivot data refresh does not use it.</span></span>  
  
9. <span data-ttu-id="3f4bc-146">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-146">Click **Next**.</span></span>  
  
10. <span data-ttu-id="3f4bc-147">**보안 저장소 대상 응용 프로그램의 자격 증명 필드를 지정** 하십시오. 페이지에서 기본값을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-147">In the **Specify the credentials fields for your Secure Store Target application** page, accept the default values.</span></span> <span data-ttu-id="3f4bc-148">필드 이름 및 유형은 Windows 사용자 이름 및 Windows 암호여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-148">Field names and types should be Windows User Name and Windows Password.</span></span>  
  
11. <span data-ttu-id="3f4bc-149">다음을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-149">Click Next.</span></span>  
  
12. <span data-ttu-id="3f4bc-150">대상 애플리케이션 관리자에서 대상 애플리케이션 설정에 대한 관리 권한을 가져야 하는 SharePoint 사용자의 Windows 도메인 사용자 계정을 지정합니다(예: 멤버 목록에 계정을 추가 또는 제거하는 권한).</span><span class="sxs-lookup"><span data-stu-id="3f4bc-150">In Target Application Administrators, specify the Windows domain user accounts of SharePoint users who should have administrative access to target application settings (for example, the ability to add or remove accounts from the Members list).</span></span>  
  
13. <span data-ttu-id="3f4bc-151">멤버에서 다음 사용자 및 그룹 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-151">In Members, add the following user and group accounts:</span></span>  
  
    1.  <span data-ttu-id="3f4bc-152">애플리케이션 작성자 권한으로 Windows 사용자 계정을 멤버 목록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-152">As the person creating the application, add your Windows user account to the Members list.</span></span>  
  
    2.  <span data-ttu-id="3f4bc-153">데이터 새로 고침을 실행하도록 예약할 때 자격 증명을 검색할 수 있도록 PowerPivot 서비스 애플리케이션의 애플리케이션 풀 ID를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-153">Add the application pool identity of the PowerPivot service application so that it can retrieve the credentials when data refresh is scheduled to run.</span></span> <span data-ttu-id="3f4bc-154">응용 프로그램 풀 id를 보려면 **서비스 응용 프로그램 관리**로 이동 하 여 이름 옆에 있는 빈 공간을 클릭 하 여 PowerPivot 서비스 응용 프로그램을 선택 하 고 **속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-154">To view the application pool identity, go to **Manage service applications**, select the PowerPivot service application by clicking the empty space next to the name (this selects the row), and then click **Properties**.</span></span> <span data-ttu-id="3f4bc-155">이 페이지에 표시되는 보안 계정이 대상 애플리케이션의 멤버로 추가할 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-155">The security account that appears on this page is the account to add as a member of the target application.</span></span>  
  
    3.  <span data-ttu-id="3f4bc-156">데이터 새로 고침 일정에서 이 대상 애플리케이션을 사용할 Windows 사용자 및 그룹 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-156">Add Windows user and group accounts that will be entering this target application in data refresh schedules.</span></span>  
  
14. <span data-ttu-id="3f4bc-157">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-157">Click **OK**.</span></span>  
  
15. <span data-ttu-id="3f4bc-158">방금 만든 대상 응용 프로그램을 선택 하 고 아래쪽 화살표를 클릭 한 다음 **자격 증명 설정을 선택 합니다.**</span><span class="sxs-lookup"><span data-stu-id="3f4bc-158">Select the target application you just created, click the down arrow and select **Set Credentials.**</span></span>  
  
16. <span data-ttu-id="3f4bc-159">자격 증명 소유자에서 자격 증명 소유자 목록이 읽기 전용인 것을 주목하십시오.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-159">In Credential Owner, notice that the list of credential owners is read-only.</span></span> <span data-ttu-id="3f4bc-160">자격 증명에 대해 소유권을 가진 계정은 대상 애플리케이션의 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-160">The accounts who have ownership over the credentials are the members of the target application.</span></span> <span data-ttu-id="3f4bc-161">자격 증명 소유자를 추가 또는 제거하려면 대상 애플리케이션 멤버 목록에 계정을 추가 또는 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-161">To add or remove a credential owner, you must add or remove accounts from the target application members list.</span></span>  
  
     <span data-ttu-id="3f4bc-162">Windows 사용자 이름 및 Windows 암호에 데이터 새로 고침을 실행하는 데 사용할 Windows 사용자 계정의 자격 증명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-162">In Windows User Name and Windows Password, type credentials of Windows user account that will be used to run data refresh.</span></span>  
  
17. <span data-ttu-id="3f4bc-163">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-163">Click **OK**.</span></span>  
  
###  <a name="step-2-grant-contribute-permissions-to-the-account"></a><a name="bkmk_grant"></a><span data-ttu-id="3f4bc-164">2 단계: 계정에 참가 권한 부여</span><span class="sxs-lookup"><span data-stu-id="3f4bc-164">Step 2: Grant Contribute permissions to the account</span></span>  
 <span data-ttu-id="3f4bc-165">저장된 자격 증명을 사용하려면 먼저 해당 계정으로 사용할 PowerPivot 통합 문서에 대한 참가 권한을 계정에 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-165">Before you can use the stored credentials, the account must be assigned Contribute permissions on any PowerPivot workbook for which it is used.</span></span> <span data-ttu-id="3f4bc-166">이 권한 수준은 라이브러리에서 통합 문서를 열고 데이터를 새로 고친 후 다시 라이브러리에 저장하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-166">This permission level is necessary to open the workbook from a library and then save it back to the library after the data is refreshed.</span></span>  
  
 <span data-ttu-id="3f4bc-167">사용 권한 할당은 사이트 모음 관리자가 수행하는 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-167">Assigning permissions is a step that is performed by the site collection administrator.</span></span> <span data-ttu-id="3f4bc-168">SharePoint 사용 권한은 루트 사이트 모음이나 개별 문서 및 항목을 포함하여 루트 사이트 모음 아래의 모든 수준에서 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-168">SharePoint permissions can be assigned at the root site collection or at any level below that, including on individual documents and items.</span></span> <span data-ttu-id="3f4bc-169">사용 권한 설정 방법은 사용 권한의 세분화 정도에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-169">How you set permissions will vary depending on how granular you need them to be.</span></span> <span data-ttu-id="3f4bc-170">다음 단계에서는 사용 권한을 부여하는 한 가지 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-170">The following steps show you one approach for granting permissions.</span></span>  
  
1.  <span data-ttu-id="3f4bc-171">SharePoint 사이트의 사이트 작업에서 **사이트 사용 권한**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-171">On a SharePoint site, in Site Actions, click **Site Permissions**.</span></span>  
  
2.  <span data-ttu-id="3f4bc-172">**권한 부여**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-172">Click **Grant Permissions**.</span></span>  
  
3.  <span data-ttu-id="3f4bc-173">사용자 선택에서 대상 애플리케이션에 지정한 Windows 도메인 사용자 계정의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-173">In Select users, type the name of the Windows domain user account that you specified in the target application.</span></span>  
  
4.  <span data-ttu-id="3f4bc-174">권한 부여에서 사용자에 **게 직접 권한 부여**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-174">In Grant Permissions, select **Grant users permission directly**.</span></span>  
  
5.  <span data-ttu-id="3f4bc-175">**참가**를 선택 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-175">Select **Contribute**, and then click **OK**.</span></span>  
  
###  <a name="step-3-grant-read-permissions-to-access-external-data-sources-used-in-data-refresh"></a><a name="bkmk_dbread"></a><span data-ttu-id="3f4bc-176">3 단계: 데이터 새로 고침에 사용 되는 외부 데이터 원본에 액세스할 수 있는 읽기 권한 부여</span><span class="sxs-lookup"><span data-stu-id="3f4bc-176">Step 3: Grant read permissions to access external data sources used in data refresh</span></span>  
 <span data-ttu-id="3f4bc-177">PowerPivot 통합 문서로 데이터를 가져올 때 외부 데이터에 대한 연결은 현재 사용자의 ID를 데이터 원본에 연결하는 데 사용하는 가장된 연결이나 트러스트된 연결을 기반으로 하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-177">When importing data into a PowerPivot workbook, connections to external data are often based on trusted connections or impersonated connections that use the identity of the current user to connect to the data source.</span></span> <span data-ttu-id="3f4bc-178">이러한 유형의 연결은 현재 사용자에게 자신이 가져오는 데이터를 읽을 수 있는 권한이 있는 경우에만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-178">These types of connections work only when the current user has permission to read the data that he or she is importing.</span></span>  
  
 <span data-ttu-id="3f4bc-179">데이터 새로 고침 시나리오에서는 데이터를 가져오는 데 사용된 것과 같은 연결 문자열이 데이터를 새로 고치는 데 다시 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-179">In a data refresh scenario, the same connection string that was used to import data is now reused to refresh the data.</span></span> <span data-ttu-id="3f4bc-180">연결 문자열이 현재 사용자를 가정하는 경우(예를 들어 Integrated_Security=SSPI를 포함하는 문자열의 경우), PowerPivot 시스템 서비스에서는 대상 애플리케이션에 지정된 사용자 ID를 현재 사용자로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-180">If the connection string assumes the current user (for example, a string that includes Integrated_Security=SSPI), then the PowerPivot System Service will pass the user identity specified in the target application as the current user.</span></span> <span data-ttu-id="3f4bc-181">이 연결은 계정에 외부 데이터 원본에 대한 읽기 권한이 있는 경우에만 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-181">This connection will only succeed if the account has read permissions on the external data source.</span></span>  
  
 <span data-ttu-id="3f4bc-182">이러한 이유로 데이터를 새로 고치는 동안 사용되는 모든 외부 데이터 원본에 대한 읽기 전용 권한을 계정에 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-182">For this reason, you must grant the account read-only permissions on all of the external data sources that are used during data refresh.</span></span>  
  
 <span data-ttu-id="3f4bc-183">조직에서 사용하는 데이터 원본의 관리자인 경우 로그인을 만들고 필요한 사용 권한을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-183">If you are an administrator of the data sources used in your organization, you can create a login and assign the necessary permissions.</span></span> <span data-ttu-id="3f4bc-184">그렇지 않은 경우에는 데이터 소유자에게 문의하여 계정 정보를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-184">Otherwise, you must contact the data owners and provide the account information.</span></span> <span data-ttu-id="3f4bc-185">대상 애플리케이션에 매핑할 Windows 도메인 사용자 계정을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-185">Be sure to specify the Windows domain user account that maps to the target application.</span></span> <span data-ttu-id="3f4bc-186">이 계정은이 항목의 "1 단계: 대상 응용 프로그램 만들기"에 지정 된 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-186">This is the account you specified in "Step 1: Create a target application" in this topic.</span></span>  
  
###  <a name="step-4-verify-account-availability-in-data-refresh-configuration-pages"></a><a name="bkmk_verify"></a><span data-ttu-id="3f4bc-187">4 단계: 데이터 새로 고침 구성 페이지에서 계정 가용성 확인</span><span class="sxs-lookup"><span data-stu-id="3f4bc-187">Step 4: Verify account availability in data refresh configuration pages</span></span>  
  
1.  <span data-ttu-id="3f4bc-188">PowerPivot 데이터가 포함되어 있는 게시된 통합 문서에 대한 데이터 새로 고침 구성 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-188">Open a data refresh configuration page for a published workbook that contains PowerPivot data.</span></span> <span data-ttu-id="3f4bc-189">페이지를 여는 방법에 대 한 지침은 [데이터 새로 고침 예약 &#40;SharePoint용 PowerPivot&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-189">For instructions on how to open the page, see [Schedule a Data Refresh &#40;PowerPivot for SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md).</span></span>  
  
2.  <span data-ttu-id="3f4bc-190">데이터 새로 고침 구성 페이지에서 **데이터 원본에 로그온 하기 위해 보안 저장소 서비스 (SSS)에 저장 된 자격 증명을 사용 하 여 연결** 옵션을 사용 하도록 설정 했는지 확인 하 고 대상 응용 프로그램의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-190">Verify that the **Connect using the credentials saved in Secure Store Service (SSS) to log on to the data source** option is enabled in the data refresh configuration page, and then enter the name of the target application.</span></span>  
  
3.  <span data-ttu-id="3f4bc-191">**가능한 빨리 새로 고치십시오** . 확인란을 선택 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-191">Select the **Also refresh as soon as possible** checkbox, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="3f4bc-192">통합 문서가 포함 된 라이브러리에서 통합 문서를 선택 하 고 오른쪽에 표시 되는 아래쪽 화살표를 클릭 한 다음 **PowerPivot 데이터 새로 고침 관리**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-192">In the library that contains the workbook, select the workbook, click the down arrow that appears to right, and then select **Manage PowerPivot Data Refresh**.</span></span> <span data-ttu-id="3f4bc-193">데이터 새로 고침 작업이 많은 데이터를 반환하는 경우 몇 분을 기다려야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-193">You might need to wait several minutes if the data refresh job is returning a large amount of data.</span></span>  
  
 <span data-ttu-id="3f4bc-194">오류가 발생 하는 경우 데이터 새로 고침 기록 페이지에서 **일정 구성** 을 클릭 하 여 다른 자격 증명을 시도할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-194">If an error occurs, you can click **Configure schedule** in the data refresh history page to try different credentials.</span></span> <span data-ttu-id="3f4bc-195">또한 원래 통합 문서의 데이터 원본 연결 정보를 검사하여 데이터를 새로 고치는 동안 사용되는 연결 문자열을 확인해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-195">You might also need to inspect the data source connection information in the original workbook to view the connection string that is used during data refresh.</span></span> <span data-ttu-id="3f4bc-196">연결 문자열은 문제를 해결하는 데 사용할 수 있는 데이터베이스와 서버 위치에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-196">The connection string will provide information about the server location and database that you can use to troubleshoot the problem.</span></span>  
  
 <span data-ttu-id="3f4bc-197">문제 해결에 대 한 자세한 내용은 TechNet Wiki의 [PowerPivot 데이터 새로 고침 문제 해결](https://go.microsoft.com/fwlink/p/?LinkID=223279) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-197">For more information about troubleshooting, see [Troubleshooting PowerPivot Data Refresh](https://go.microsoft.com/fwlink/p/?LinkID=223279) on the TechNet Wiki.</span></span>  
  
##  <a name="configure-a-predefined-account-for-accessing-external-or-third-party-data-sources"></a><a name="config3rd"></a><span data-ttu-id="3f4bc-198">외부 또는 타사 데이터 원본에 액세스 하기 위한 미리 정의 된 계정 구성</span><span class="sxs-lookup"><span data-stu-id="3f4bc-198">Configure a predefined account for accessing external or third-party data sources</span></span>  
 <span data-ttu-id="3f4bc-199">데이터베이스 서버는 자체 인증 방법과 함께 제공되는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-199">Database servers often come with their own authentication methods.</span></span> <span data-ttu-id="3f4bc-200">데이터 새로 고침 중에 외부 데이터 원본에 액세스하는 데 데이터베이스 자격 증명이 필요한 PowerPivot 통합 문서가 있을 경우 자격 증명에 대한 대상 애플리케이션 ID를 만든 다음 일정 데이터 새로 고침 페이지의 데이터 원본 섹션에서 대상 애플리케이션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-200">If you have a PowerPivot workbook that requires database credentials to access an external data source during data refresh, you can create a target application ID for the credentials, and then specify the target application in the Data Sources section of the schedule data refresh page.</span></span>  
  
 <span data-ttu-id="3f4bc-201">이 단계는 PowerPivot 통합 문서에 이미 포함된 데이터베이스 자격 증명을 재정의할 수 있는 옵션을 제공하려는 경우에만 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-201">This step is only necessary if you want to provide users with an option of overriding the database credentials that are already embedded in the PowerPivot workbook.</span></span>  
  
 <span data-ttu-id="3f4bc-202">이 단계는 연결 문자열에 사용자 이름과 암호가 이미 포함되어 있는 경우에만 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-202">This step only works if the connection string already includes a user name and password.</span></span> <span data-ttu-id="3f4bc-203">연결 문자열에 자격 증명을 포함하는 것은 비교적 흔하지 않으므로 이 옵션의 활용 권한은 어느 정도 제한적입니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-203">Note that having credentials in the connection string is relatively uncommon, so your ability to make use of this option is somewhat limited.</span></span> <span data-ttu-id="3f4bc-204">데이터베이스 인증을 사용하여 데이터 원본에 연결하는 경우 연결 문자열에 사용자 ID와 암호만 있는 경우가 대부분입니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-204">In most cases, you will only have a user ID and password in the connection string if you are using database authentication to connect to the data source.</span></span> <span data-ttu-id="3f4bc-205">연결 문자열에 사용자 ID와 암호가 포함 되어 있는지 확인 하는 방법에 대 한 자세한 내용은 [SharePoint 2010를 사용 하 여 PowerPivot 데이터 새로 고침](powerpivot-data-refresh-with-sharepoint-2010.md)의 "일정을 만들고 외부 데이터에 액세스할 수 있는 권한 부여" 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-205">For more information about how to check the connection string to see if it includes a User ID and password, see the "Grant permissions to create schedules and access external data" section in [PowerPivot Data Refresh with SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md).</span></span>  
  
1.  <span data-ttu-id="3f4bc-206">중앙 관리의 애플리케이션 관리에서 **서비스 애플리케이션 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-206">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="3f4bc-207">**보안 저장소 서비스**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-207">Click **Secure Store Service**.</span></span>  
  
3.  <span data-ttu-id="3f4bc-208">대상 응용 프로그램 관리에서 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-208">In Manage Target Applications, click **New**.</span></span>  
  
4.  <span data-ttu-id="3f4bc-209">대상 애플리케이션 ID에 텍스트 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-209">In Target application ID, type a text string.</span></span> <span data-ttu-id="3f4bc-210">이 문자열은 고유하면서 기억하기도 쉬워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-210">The string must be unique, but it should also be easy to remember.</span></span> <span data-ttu-id="3f4bc-211">사용자는 이 애플리케이션에 저장된 자격 증명을 사용할 때마다 데이터 새로 고침 일정 페이지에서 이 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-211">Users will type this string in data refresh schedule pages whenever they want to use the credentials that are stored in this application.</span></span>  
  
5.  <span data-ttu-id="3f4bc-212">표시 이름에 응용 프로그램을 설명하는 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-212">In Display Name, enter a descriptive name.</span></span> <span data-ttu-id="3f4bc-213">이 이름은 표시용으로만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-213">This name is used for display purposes only.</span></span> <span data-ttu-id="3f4bc-214">이 이름은 데이터 새로 고침 일정에서 대상 애플리케이션을 지정하는 데 사용되는 이름이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-214">It is not used to specify the target application in a data refresh schedule.</span></span>  
  
6.  <span data-ttu-id="3f4bc-215">담당자 전자 메일에 사용자의 전자 메일 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-215">In Contact Email, type your e-mail address.</span></span>  
  
7.  <span data-ttu-id="3f4bc-216">대상 응용 프로그램 형식에서 **그룹**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-216">In Target Application Type, select **Group**.</span></span>  
  
8.  <span data-ttu-id="3f4bc-217">대상 애플리케이션 페이지 URL을 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-217">Skip Target Application Page URL.</span></span> <span data-ttu-id="3f4bc-218">PowerPivot 데이터 새로 고침에서 이 URL을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-218">PowerPivot data refresh does not use it.</span></span>  
  
9. <span data-ttu-id="3f4bc-219">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-219">Click **Next**.</span></span>  
  
10. <span data-ttu-id="3f4bc-220">**보안 저장소 대상 응용 프로그램에 대 한 자격 증명 필드 지정** 페이지에서 데이터 원본에서 Windows 인증을 사용 하는 경우에만 기본값을 그대로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-220">In the **Specify the credentials fields for your Secure Store Target application** page, accept the default values only if the data source uses Windows authentication.</span></span> <span data-ttu-id="3f4bc-221">그렇지 않으면 데이터 원본에 적합한 필드 유형을 선택한 다음 유형에 맞게 필드 이름을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-221">Otherwise, choose the field types that are valid for your data source, and then edit the field names to match the type.</span></span>  
  
     <span data-ttu-id="3f4bc-222">예를 들어 필드 이름에 SQL Server 사용자 이름 및 SQL Server 사용자 암호를 지정한 다음 필드 유형에 사용자 이름 및 암호를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-222">For example, you might specify SQL Server User Name and SQL Server User Password for field names, and then choose User Name and Password for field types.</span></span>  
  
11. <span data-ttu-id="3f4bc-223">다음을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-223">Click Next.</span></span>  
  
12. <span data-ttu-id="3f4bc-224">대상 애플리케이션 관리자에서 애플리케이션 설정에 대한 관리 권한을 가져야 하는 SharePoint 사용자의 Windows 도메인 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-224">In Target Application Administrators, specify the Windows domain user accounts of SharePoint users who should have administrative access to the application settings.</span></span>  
  
13. <span data-ttu-id="3f4bc-225">멤버에서 다음 사용자 및 그룹 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-225">In Members, add the following user and group accounts:</span></span>  
  
    1.  <span data-ttu-id="3f4bc-226">애플리케이션 작성자 권한으로 Windows 사용자 계정을 멤버 목록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-226">As the person creating the application, add your Windows user account to the Members list.</span></span>  
  
    2.  <span data-ttu-id="3f4bc-227">대상 애플리케이션을 사용하여 저장된 자격 증명에 액세스할 각 PowerPivot 서비스 애플리케이션의 애플리케이션 풀 ID를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-227">Add the application pool identity of each PowerPivot service application that will be using the target application to access its stored credentials.</span></span> <span data-ttu-id="3f4bc-228">Id를 보려면 **서비스 응용 프로그램 관리**로 이동 하 여 이름 옆에 있는 빈 공간을 클릭 하 여 PowerPivot 서비스 응용 프로그램을 선택 하 고 (행을 선택 하는 경우) **속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-228">To view the identity, go to **Manage service applications**, select the PowerPivot service application by clicking the empty space next to the name (this selects the row), and then click **Properties**.</span></span> <span data-ttu-id="3f4bc-229">이 페이지에 표시되는 보안 계정이 대상 애플리케이션의 멤버로 추가할 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-229">The security account that appears on this page is the account that you want to add as a member of the target application.</span></span>  
  
    3.  <span data-ttu-id="3f4bc-230">데이터 새로 고침 일정 페이지의 데이터 원본 섹션에서 이 대상 애플리케이션을 입력할 Windows 사용자 및 그룹 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-230">Add Windows user and group accounts that will be entering this target application in the data sources section of a data refresh schedule page.</span></span>  
  
14. <span data-ttu-id="3f4bc-231">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-231">Click **OK**.</span></span>  
  
15. <span data-ttu-id="3f4bc-232">방금 만든 대상 응용 프로그램을 선택 하 고 아래쪽 화살표를 클릭 한 다음 **자격 증명 설정을 선택 합니다.**</span><span class="sxs-lookup"><span data-stu-id="3f4bc-232">Select the target application you just created, click the down arrow and select **Set Credentials.**</span></span>  
  
16. <span data-ttu-id="3f4bc-233">데이터 원본에 연결하는 데 사용할 자격 증명을 입력합니다(예: SQL Server 로그인의 사용자 이름 및 암호).</span><span class="sxs-lookup"><span data-stu-id="3f4bc-233">Enter the credentials that will be used to connect to the data source (for example, the user name and password of a SQL Server login).</span></span>  
  
17. <span data-ttu-id="3f4bc-234">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3f4bc-234">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f4bc-235">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3f4bc-235">See Also</span></span>  
 <span data-ttu-id="3f4bc-236">[데이터 새로 고침 예약 &#40;SharePoint용 PowerPivot&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="3f4bc-236">[Schedule a Data Refresh &#40;PowerPivot for SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md) </span></span>  
 [<span data-ttu-id="3f4bc-237">SharePoint 2010에서 PowerPivot 데이터 새로 고침</span><span class="sxs-lookup"><span data-stu-id="3f4bc-237">PowerPivot Data Refresh with SharePoint 2010</span></span>](powerpivot-data-refresh-with-sharepoint-2010.md)  
  
  

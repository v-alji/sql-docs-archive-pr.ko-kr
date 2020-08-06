---
title: 데이터 새로 고침 예약 및 Windows 인증을 지원 하지 않는 데이터 원본 (SharePoint용 PowerPivot) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d8d875bc-7823-46b7-a939-867cefd4de12
author: minewiskan
ms.author: owend
ms.openlocfilehash: 63e37dec6f334395c0c1812c6f76d750c16c53ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651316"
---
# <a name="schedule-data-refresh-and-data-sources-that-do-not-support-windows-authentication-powerpivot-for-sharepoint"></a><span data-ttu-id="d4b4a-102">데이터 새로 고침 예약 및 Windows 인증을 지원하지 않는 데이터 원본(SharePoint용 PowerPivot)</span><span class="sxs-lookup"><span data-stu-id="d4b4a-102">Schedule Data Refresh and Data Sources That Do Not Support Windows Authentication (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="d4b4a-103">이 항목에서는 Windows 인증을 지원하지 **않는** 데이터 원본을 사용할 수 있는 SharePoint용 PowerPivot 데이터 새로 고침 예약 워크플로에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-103">This topic describes a workflow of PowerPivot for SharePoint schedule data fresh that can use data sources that do **NOT** support Windows Authentication.</span></span> <span data-ttu-id="d4b4a-104">예를 들어 Oracle 또는 IDM DB2 데이터 원본의 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-104">For example Oracle or IDM DB2 data sources.</span></span> <span data-ttu-id="d4b4a-105">이 항목의 그림 및 단계는 Oracle 데이터 원본을 참조하지만 동일한 워크플로가 다른 데이터 원본에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-105">The illustrations and steps in this topic reference Oracle data sources but the same workflow applies to other data sources.</span></span>  
  
||  
|-|  
|<span data-ttu-id="d4b4a-106">**[!INCLUDE[applies](../../includes/applies-md.md)]** Sharepoint 2010 &#124; SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010 &#124; SharePoint 2013.</span></span>|  
  
 <span data-ttu-id="d4b4a-107">**개요:** 보안 저장소 대상 애플리케이션을 두 개 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-107">**Overview:** Create two Secure Store Target Applications.</span></span> <span data-ttu-id="d4b4a-108">Windows 자격 증명을 사용하는 첫 번째 대상 애플리케이션(PowerPivotDataRefresh)을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-108">Configure the first target application (PowerPivotDataRefresh) to use Windows credentials.</span></span> <span data-ttu-id="d4b4a-109">Windows 인증을 지원하지 않는 데이터 원본(예: Oracle 데이터베이스)에 대한 자격 증명을 사용하여 두 번째 대상 애플리케이션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-109">Configure the second target application with the credentials for a data source that does not support windows authentication, for example, an Oracle database.</span></span> <span data-ttu-id="d4b4a-110">두 번째 대상 애플리케이션도 무인 데이터 새로 고침 계정에는 첫 번째 대상 애플리케이션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-110">The second target application also uses the first target application for the unattended data refresh account.</span></span>  
  
 <span data-ttu-id="d4b4a-111">![as_powerpivot_refresh_no_windows_auth](../media/as-powerpivot-refresh-no-windows-auth.gif "as_powerpivot_refresh_no_windows_auth")</span><span class="sxs-lookup"><span data-stu-id="d4b4a-111">![as_powerpivot_refresh_no_windows_auth](../media/as-powerpivot-refresh-no-windows-auth.gif "as_powerpivot_refresh_no_windows_auth")</span></span>  
  
-   <span data-ttu-id="d4b4a-112">**(1) PowerPivotDatarefresh:** Windows 인증으로 설정된 보안 저장소 대상 애플리케이션 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-112">**(1) PowerPivotDatarefresh:** A Secure Store Target Application ID that is set with windows authentication.</span></span>  
  
-   <span data-ttu-id="d4b4a-113">**(2) OracleAuthentication:** Oracle 자격 증명으로 설정된 보안 저장소 대상 애플리케이션 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-113">**(2) OracleAuthentication:** A Secure Store Target Application ID that is set with Oracle credentials.</span></span>  
  
-   <span data-ttu-id="d4b4a-114">**(3)** PowerPivot 서비스 응용 프로그램은 **무인 데이터 새로 고침 계정**에 대해 대상 응용 프로그램 "PowerPivotDataRefresh"를 사용 하도록 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-114">**(3)** The PowerPivot Service application is configure to use the target application "PowerPivotDataRefresh" for the **Unattended Data Refresh Account**.</span></span>  
  
-   <span data-ttu-id="d4b4a-115">**(4)** PowerPivot 통합 문서는 Oracle 데이터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-115">**(4)** PowerePivot Workbook uses Oracle data.</span></span> <span data-ttu-id="d4b4a-116">통합 문서 새로 고침 설정은 데이터 원본 연결 자격 증명에 대상 애플리케이션 **(2)** 를 사용하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-116">The workbook refresh settings specify the data source connection to use the target application **(2)** for credentials.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d4b4a-117">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="d4b4a-117">Prerequisites</span></span>  
  
-   <span data-ttu-id="d4b4a-118">PowerPivot 서비스 애플리케이션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-118">A PowerPivot Service Application exists.</span></span>  
  
-   <span data-ttu-id="d4b4a-119">Secure Store Service 애플리케이션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-119">A Secure Store Service Application exists.</span></span>  
  
-   <span data-ttu-id="d4b4a-120">PowerPivot 데이터 모델이 포함된 Excel 통합 문서가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-120">An Excel workbook with a PowerPivot data model exists.</span></span>  
  
## <a name="to-create-a-target-application-id-that-uses-windows-authentication"></a><span data-ttu-id="d4b4a-121">Windows 인증을 사용하는 대상 애플리케이션 ID를 만들려면</span><span class="sxs-lookup"><span data-stu-id="d4b4a-121">To Create a Target Application ID that uses Windows Authentication</span></span>  
  
1.  <span data-ttu-id="d4b4a-122">SharePoint 중앙 관리에서 **서비스 응용 프로그램 관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-122">In SharePoint Central administration, click **Manage Service Applications**.</span></span>  
  
2.  <span data-ttu-id="d4b4a-123">Secure Store Service 애플리케이션의 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-123">Click the name of your secure store service application.</span></span>  
  
3.  <span data-ttu-id="d4b4a-124">**관리** 페이지에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-124">On the **Manage** page, click **New**.</span></span> <span data-ttu-id="d4b4a-125">![as_powerpivot_refresh_sss_new_target_application](../media/as-powerpivot-refresh-sss-new-target-application.gif "as_powerpivot_refresh_sss_new_target_application")</span><span class="sxs-lookup"><span data-stu-id="d4b4a-125">![as_powerpivot_refresh_sss_new_target_application](../media/as-powerpivot-refresh-sss-new-target-application.gif "as_powerpivot_refresh_sss_new_target_application")</span></span>  
  
4.  <span data-ttu-id="d4b4a-126">**새 보안 저장소 대상 애플리케이션 만들기** 페이지에서 다음 값을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-126">On the **Create New Secure Store Target Application** page, configure the following values:</span></span>  
  
    -   <span data-ttu-id="d4b4a-127">**대상 애플리케이션 ID:** PowerPivotDataRefresh</span><span class="sxs-lookup"><span data-stu-id="d4b4a-127">**Target Application ID:** PowerPivotDataRefresh.</span></span>  
  
    -   <span data-ttu-id="d4b4a-128">**표시 이름:** PowerPivotDataRefresh</span><span class="sxs-lookup"><span data-stu-id="d4b4a-128">**Display Name:** PowerPivotDataRefresh.</span></span>  
  
    -   <span data-ttu-id="d4b4a-129">**담당자 메일:** ?</span><span class="sxs-lookup"><span data-stu-id="d4b4a-129">**Contact E-mail:** ?</span></span>  
  
    -   <span data-ttu-id="d4b4a-130">**대상 애플리케이션 형식:** 그룹</span><span class="sxs-lookup"><span data-stu-id="d4b4a-130">**Target Application Type:** Group.</span></span>  
  
    -   <span data-ttu-id="d4b4a-131">**대상 애플리케이션 페이지 URL:** 없음</span><span class="sxs-lookup"><span data-stu-id="d4b4a-131">**Target Application Page URL:** None.</span></span>  
  
5.  <span data-ttu-id="d4b4a-132">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-132">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="d4b4a-133">자격 증명 페이지에서 **Windows 사용자 이름** 및 **Windows 암호**의 두 기본 필드 이름과 필드 형식은 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-133">On the Credentials page, leave the two default field names and field types for **Windows User Name** and **Windows Password**.</span></span>  
  
7.  <span data-ttu-id="d4b4a-134">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-134">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="d4b4a-135">**멤버 자격 설정** 페이지에서 하나 이상의 **대상 애플리케이션 관리자** 를 추가한 다음 대상 애플리케이션에 대한 액세스 권한이 필요한 멤버를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-135">On the **Membership Settings** page, add at least one **Target Application Administrator** and then add members that need access to the target application.</span></span>  
  
9. <span data-ttu-id="d4b4a-136">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-136">Click **OK**.</span></span>  
  
10. <span data-ttu-id="d4b4a-137">새 대상 애플리케이션 ID가 목록에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-137">The new Target Application ID is added to the list.</span></span> <span data-ttu-id="d4b4a-138">대상 응용 프로그램 ID를 선택 하 고 **자격 증명 설정**![as_powerpivot_refresh_sss_set_key](../media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key")을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-138">Select the Target application ID and click **Set Credentials**![as_powerpivot_refresh_sss_set_key](../media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key").</span></span>  
  
11. <span data-ttu-id="d4b4a-139">Windows 사용자 이름 및 Windows 암호를 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-139">Type the Windows User Name and Windows Password and then click **OK**.</span></span>  
  
## <a name="to-create-a-target-application-id-that-uses-oracle-credentials"></a><span data-ttu-id="d4b4a-140">Oracle 자격 증명을 사용하는 대상 애플리케이션 ID를 만들려면</span><span class="sxs-lookup"><span data-stu-id="d4b4a-140">To Create a Target Application ID that uses Oracle credentials</span></span>  
  
1.  <span data-ttu-id="d4b4a-141">SharePoint 중앙 관리에서 **서비스 응용 프로그램 관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-141">In SharePoint Central administration, click **Manage Service Applications**.</span></span>  
  
2.  <span data-ttu-id="d4b4a-142">Secure Store Service 애플리케이션의 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-142">Click the name of your Secure Store Service application.</span></span>  
  
3.  <span data-ttu-id="d4b4a-143">**관리** 페이지에서 **새로 만들기**![as_powerpivot_refresh_sss_new_target_application](../media/as-powerpivot-refresh-sss-new-target-application.gif "as_powerpivot_refresh_sss_new_target_application")를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-143">On the **Manage** page, click **New**![as_powerpivot_refresh_sss_new_target_application](../media/as-powerpivot-refresh-sss-new-target-application.gif "as_powerpivot_refresh_sss_new_target_application").</span></span>  
  
4.  <span data-ttu-id="d4b4a-144">**새 보안 저장소 대상 애플리케이션 만들기** 페이지에서 다음 값을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-144">On the **Create New Secure Store Target Application** page, configure the following values:</span></span>  
  
    -   <span data-ttu-id="d4b4a-145">**대상 애플리케이션 ID:** OracleAuthentication</span><span class="sxs-lookup"><span data-stu-id="d4b4a-145">**Target Application ID:** OracleAuthentication.</span></span>  
  
    -   <span data-ttu-id="d4b4a-146">**표시 이름:** OracleAuthentication</span><span class="sxs-lookup"><span data-stu-id="d4b4a-146">**Display Name:** OracleAuthentication.</span></span>  
  
    -   <span data-ttu-id="d4b4a-147">**담당자 메일:** ?</span><span class="sxs-lookup"><span data-stu-id="d4b4a-147">**Contact E-mail:** ?</span></span>  
  
    -   <span data-ttu-id="d4b4a-148">**대상 애플리케이션 형식:** 그룹</span><span class="sxs-lookup"><span data-stu-id="d4b4a-148">**Target Application Type:** Group.</span></span>  
  
    -   <span data-ttu-id="d4b4a-149">**대상 애플리케이션 페이지 URL:** 없음</span><span class="sxs-lookup"><span data-stu-id="d4b4a-149">**Target Application Page URL:** None.</span></span>  
  
5.  <span data-ttu-id="d4b4a-150">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-150">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="d4b4a-151">**자격 증명** 페이지에서 첫 번째 필드 이름을로 변경 하 `Oracle User ID` 고 **필드 형식을** 로 변경 합니다 `User Name` .</span><span class="sxs-lookup"><span data-stu-id="d4b4a-151">On the **Credentials** page, change the first field name to `Oracle User ID` and change the **Field Type** to `User Name`.</span></span>  
  
     <span data-ttu-id="d4b4a-152">두 번째 필드 이름을로 변경 하 `Oracle Password` 고 **필드 형식을** 로 변경 합니다 `Password` .</span><span class="sxs-lookup"><span data-stu-id="d4b4a-152">Change the second field name to `Oracle Password` and the **Field Type** to `Password`.</span></span>  
  
7.  <span data-ttu-id="d4b4a-153">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-153">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="d4b4a-154">**멤버 자격 설정** 페이지에서 하나 이상의 **대상 애플리케이션 관리자** 를 추가한 다음 대상 애플리케이션에 대한 액세스 권한이 필요한 멤버를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-154">On the **Membership Settings** page, add at least one **Target Application Administrator** and then add members that need access to the target application.</span></span>  
  
9. <span data-ttu-id="d4b4a-155">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-155">Click **OK**.</span></span>  
  
10. <span data-ttu-id="d4b4a-156">새 대상 애플리케이션 ID가 목록에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-156">The new Target Application ID is added to the list.</span></span> <span data-ttu-id="d4b4a-157">대상 응용 프로그램 ID를 선택 하 고 **자격 증명 설정**![as_powerpivot_refresh_sss_set_key](../media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key")을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-157">Select the Target application ID and click **Set Credentials**![as_powerpivot_refresh_sss_set_key](../media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key").</span></span>  
  
11. <span data-ttu-id="d4b4a-158">Oracle 사용자 ID 및 Oracle 암호를 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-158">Type the Oracle User ID and Oracle Password and then click **OK**.</span></span>  
  
 <span data-ttu-id="d4b4a-159">자세한 내용은 [SQL Server 인증으로 보안 저장소 사용 (SharePoint Server 2013) ()](https://technet.microsoft.com/library/gg298949.aspx) 에서 "SQL Server 인증을 위한 대상 응용 프로그램을 만들려면" 섹션을 참조 하세요 https://technet.microsoft.com/library/gg298949.aspx) .</span><span class="sxs-lookup"><span data-stu-id="d4b4a-159">For more information, see section "To Create a target application for SQL Server Authentication" in [Use Secure Store with SQL Server Authentication (SharePoint Server 2013)](https://technet.microsoft.com/library/gg298949.aspx) (https://technet.microsoft.com/library/gg298949.aspx).</span></span>  
  
## <a name="to-configure-the-powerpivot-service-application"></a><span data-ttu-id="d4b4a-160">PowerPivot 서비스 애플리케이션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="d4b4a-160">To Configure the PowerPivot Service Application</span></span>  
  
1.  <span data-ttu-id="d4b4a-161">SharePoint 중앙 관리에서 서비스 애플리케이션 관리를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-161">In SharePoint central administration, click Manage Service Applications.</span></span>  
  
2.  <span data-ttu-id="d4b4a-162">PowerPivot 서비스 응용 프로그램의 이름을 클릭 합니다 (예: "기본 PowerPivot 서비스 응용 프로그램").</span><span class="sxs-lookup"><span data-stu-id="d4b4a-162">Click the name of your PowerPivot Service Application, for example "Default PowerPivot Service Application".</span></span>  
  
3.  <span data-ttu-id="d4b4a-163">동작 섹션에서 **서비스 애플리케이션 설정 구성** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-163">Click **Configure service application settings** in the Actions section.</span></span>  
  
4.  <span data-ttu-id="d4b4a-164">**데이터 새로 고침** 섹션에서 **PowerPivot 무인 데이터 새로 고침 계정을**로 설정 하 `PowerPivotDataRefresh` 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-164">In the **Data Refresh** section, set the **PowerPivot Unattended Data Refresh Account**to`PowerPivotDataRefresh` and then click **OK**.</span></span>  
  
     <span data-ttu-id="d4b4a-165">![as_powerpivot_refresh_new_refresh_acount](../media/as-powerpivot-refresh-new-refresh-acount.gif "as_powerpivot_refresh_new_refresh_acount")</span><span class="sxs-lookup"><span data-stu-id="d4b4a-165">![as_powerpivot_refresh_new_refresh_acount](../media/as-powerpivot-refresh-new-refresh-acount.gif "as_powerpivot_refresh_new_refresh_acount")</span></span>  
  
## <a name="to-configure-the-workbook"></a><span data-ttu-id="d4b4a-166">통합 문서를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="d4b4a-166">To configure the workbook</span></span>  
  
1.  <span data-ttu-id="d4b4a-167">PowerPivot 갤러리에서 통합 문서를 찾은 다음 **데이터 새로 고침 관리**![as_powerpivot_refresh_manage_reresh](../media/as-powerpivot-refresh-manage-reresh.gif "as_powerpivot_refresh_manage_reresh")를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-167">Browse to your workbook in the PowerPivot Gallery and click **Manage Data Refresh**![as_powerpivot_refresh_manage_reresh](../media/as-powerpivot-refresh-manage-reresh.gif "as_powerpivot_refresh_manage_reresh").</span></span>  
  
2.  <span data-ttu-id="d4b4a-168">**데이터 새로 고침 기록** 페이지가 표시되면 **일정 구성**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-168">If you see the **Data Refresh History** page, click **Configure Schedule**.</span></span>  
  
3.  <span data-ttu-id="d4b4a-169">**사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-169">Click **Enable**.</span></span>  
  
4.  <span data-ttu-id="d4b4a-170">**가능한 빨리 새로 고치십시오.** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-170">Click **Also Refresh as soon as possible**.</span></span>  
  
5.  <span data-ttu-id="d4b4a-171">**자격 증명** 섹션에서 **관리자가 구성한 데이터 새로 고침 계정 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-171">In the **Credentials** section, click **Use the Data refresh account configured by the administrator**.</span></span>  
  
6.  <span data-ttu-id="d4b4a-172">**모든 데이터 원본**의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-172">Clear **All data sources**.</span></span>  
  
7.  <span data-ttu-id="d4b4a-173">Oracle 데이터를 사용하는 데이터 원본에 대해 **새로 고침** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-173">Select **Refresh** for the data source that uses the Oracle data.</span></span> <span data-ttu-id="d4b4a-174">데이터 원본 이름의 이름은 Microsoft Excel의 **데이터**, **연결**, **속성** 메뉴에서 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-174">The name of the data source name can be changed in Microsoft Excel in the **Data**, **Connections**, **Properties** menu.</span></span>  
  
8.  <span data-ttu-id="d4b4a-175">해당 데이터 원본에서 **기본 일정 사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-175">Under your data source, Select **Use Default Schedule**.</span></span>  
  
9. <span data-ttu-id="d4b4a-176">**데이터 원본에 로그온하려면 SSS(Secure Store Service)에 저장된 자격 증명을 사용하여 연결합니다. SSS ID 상자에 자격 증명을 조회하는 데 사용되는 ID를 입력합니다**.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-176">Select **Connect using the credentials saved in Secure Store Service (SSS) to log on to the data source. Enter the ID used to look up the credentials in the SSS ID box**.</span></span>  
  
10. <span data-ttu-id="d4b4a-177">**ID:** 상자에을 입력 `OracleAuthentication` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-177">In the **ID:** box, type `OracleAuthentication`.</span></span>  
  
11. <span data-ttu-id="d4b4a-178">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-178">Click **OK**.</span></span>  
  
     <span data-ttu-id="d4b4a-179">`The provided Secure Store target application is either incorrectly configured or does not exist`과(와) 유사한 오류 메시지가 표시될 경우.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-179">If you see an error message similar to: `The provided Secure Store target application is either incorrectly configured or does not exist`.</span></span>  
  
     <span data-ttu-id="d4b4a-180">일반적인 해결 방법으로는 다음 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-180">The two common solutions are:</span></span>  
  
    -   <span data-ttu-id="d4b4a-181">대상 애플리케이션 ID가 올바른지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-181">Verify that the Target Application ID is correct.</span></span>  
  
    -   <span data-ttu-id="d4b4a-182">대상 애플리케이션에 대한 자격 증명 설정을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-182">Verify that you set credentials for the Target Application.</span></span>  
  
## <a name="to-verify-data-refresh-with-the-new-authentication"></a><span data-ttu-id="d4b4a-183">새 인증으로 데이터 새로 고침을 확인하려면</span><span class="sxs-lookup"><span data-stu-id="d4b4a-183">To Verify Data Refresh with the new authentication</span></span>  
 <span data-ttu-id="d4b4a-184">**확인**을 클릭하면 **새로 고침 기록** 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-184">When you click **ok**, you see the **Refresh History** page.</span></span> <span data-ttu-id="d4b4a-185">이전 단계에서 **가능한 빨리 새로 고치십시오.** 를 선택했으므로 몇 분 이내에 새로 고침 기록에 새 항목이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-185">Within a few minutes, you should see a new item in the refresh history because in the previous steps you selected **Also Refresh as soon as possible**.</span></span> <span data-ttu-id="d4b4a-186">타이머 작업 **PowerPivot 데이터 새로 고침 타이머 작업** 의 기본값은 1분입니다.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-186">The default value for the timer job **PowerPivot Data Refresh Timer Job** is 1 minute.</span></span> <span data-ttu-id="d4b4a-187">새로 고침 기록에 새 항목이 표시되지 않으면 몇 분 기다렸다가 브라우저를 새로 고치십시오.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-187">If you do not see a new item in the refresh history, wait a few minutes and refresh your browser.</span></span> <span data-ttu-id="d4b4a-188">여전히 새 항목이 표시되지 않으면 타이머 작업의 현재 값을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-188">If you still do not see the new item, verify the current value of the timer job.</span></span>  
  
## <a name="more-information"></a><span data-ttu-id="d4b4a-189">추가 정보</span><span class="sxs-lookup"><span data-stu-id="d4b4a-189">More Information</span></span>  
  
-   <span data-ttu-id="d4b4a-190">[SharePoint 2013에서 보안 저장소 서비스 구성](https://technet.microsoft.com/library/ee806866.aspx).</span><span class="sxs-lookup"><span data-stu-id="d4b4a-190">[Configure the Secure Store Service in SharePoint 2013](https://technet.microsoft.com/library/ee806866.aspx).</span></span>  
  
-   <span data-ttu-id="d4b4a-191">[SharePoint 2013 및 SQL Server 2012 SP1 (Analysis Services)을 사용 하 여 PowerPivot 데이터 새로 고침](https://msdn.microsoft.com/library/jj879294.aspx#bkmk_windows_auth_interactive_data_refresh)의 "예약 된 데이터 새로 고침" 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d4b4a-191">See the "Scheduled Data Refresh" section of [PowerPivot Data Refresh with SharePoint 2013 and SQL Server 2012 SP1 (Analysis Services)](https://msdn.microsoft.com/library/jj879294.aspx#bkmk_windows_auth_interactive_data_refresh).</span></span>  
  
  

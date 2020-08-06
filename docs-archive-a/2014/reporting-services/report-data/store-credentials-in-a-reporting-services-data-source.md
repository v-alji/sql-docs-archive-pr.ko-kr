---
title: Reporting Services 데이터 원본에 자격 증명 저장 | Microsoft Docs
ms.custom: ''
ms.date: 09/23/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- credentials [Reporting Services]
- security [Analysis Services], data sources
- stored credentials [Reporting Services]
- data sources [Reporting Services], stored credentials
ms.assetid: dc700922-97fa-4b30-9547-05bbbec4f09c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fccf8669d1f39d19a26b443ffcead8e86db66a34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653222"
---
# <a name="store-credentials-in-a-reporting-services-data-source"></a><span data-ttu-id="50684-102">Reporting Services 데이터 원본에 자격 증명 저장</span><span class="sxs-lookup"><span data-stu-id="50684-102">Store Credentials in a Reporting Services Data Source</span></span>
  <span data-ttu-id="50684-103">보고서에 대한 외부 데이터에 액세스하기 위해 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 보고서 서버에서 사용하는 저장된 자격 증명을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50684-103">You can configure stored credentials that a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report server uses to access external data for a report.</span></span> <span data-ttu-id="50684-104">보고서가 무인 모드로 실행되는 경우 저장된 자격 증명이 사용됩니다(예: 보고서를 전자 메일로 게시하는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 구독).</span><span class="sxs-lookup"><span data-stu-id="50684-104">Stored credentials are used if the report runs unattended, for example a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] subscription that publishes a report as an e-mail.</span></span> <span data-ttu-id="50684-105">보고서 처리가 예약되거나 트리거되면 보고서 서버는 자격 증명을 검색하고 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-105">The report server retrieves and uses the credentials when report processing is scheduled or triggered.</span></span> <span data-ttu-id="50684-106">이 항목에서는 기본 모드 및 SharePoint 모드 보고서 서버에 대해 저장된 자격 증명을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-106">This topic walks you through configuring stored credentials for both Native mode and SharePoint mode report servers.</span></span>

||
|-|
|<span data-ttu-id="50684-107">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 기본 모드 &#124; [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint 모드</span><span class="sxs-lookup"><span data-stu-id="50684-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>|

 <span data-ttu-id="50684-108">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="50684-108">**In this topic:**</span></span>

-   [<span data-ttu-id="50684-109">보고서 관련 데이터 원본에 대해 저장 된 자격 증명 구성 (기본 모드)</span><span class="sxs-lookup"><span data-stu-id="50684-109">Configure stored credentials for a report-specific data source (Native mode)</span></span>](#bkmk_stored_credentials_data_source_native)

-   [<span data-ttu-id="50684-110">보고서 관련 데이터 원본에 대해 저장 된 자격 증명 구성 (SharePoint 모드)</span><span class="sxs-lookup"><span data-stu-id="50684-110">Configure stored credentials for a report-specific data source (SharePoint mode)</span></span>](#bkmk_stored_credentials_data_source_sharepoint)

-   [<span data-ttu-id="50684-111">공유 데이터 원본에 대 한 저장 된 자격 증명 구성 (기본 모드)</span><span class="sxs-lookup"><span data-stu-id="50684-111">Configure stored credentials for a shared data source (Native mode)</span></span>](#bkmk_stored_credentials_shared_data_source_native)

-   [<span data-ttu-id="50684-112">공유 데이터 원본에 대해 저장된 자격 증명 구성(SharePoint 모드)</span><span class="sxs-lookup"><span data-stu-id="50684-112">Configure stored credentials for a shared data source (SharePoint mode)</span></span>](#bkmk_stored_credentials_shared_data_source_sharepoint)

##  <a name="security-policy-requirements-for-stored-credentials"></a><a name="bkmk_top"></a> <span data-ttu-id="50684-113">저장된 자격 증명에 대한 보안 정책 요구 사항</span><span class="sxs-lookup"><span data-stu-id="50684-113">Security policy requirements for stored credentials</span></span>
 <span data-ttu-id="50684-114">![as_powerpivot_refresh_sss_set_key](../../analysis-services/media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key") 보고서 서버의 다음 보안 정책 중 하나의 경우, 저장된 자격 증명에 대해 사용하는 계정을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-114">![as_powerpivot_refresh_sss_set_key](../../analysis-services/media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key") It is required that the account you use for stored credentials, is configured for one of the following security policies on the report server.</span></span> <span data-ttu-id="50684-115">환경에서 필요한 최저 수준의 권한을 지닌 정책을 선택하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="50684-115">It is recommended you select the policy with the minimum level of permissions you require for your environment.</span></span>

1.  <span data-ttu-id="50684-116">**로컬 로그온 허용**.</span><span class="sxs-lookup"><span data-stu-id="50684-116">**Allow log on locally**.</span></span> <span data-ttu-id="50684-117">자세한 내용은 [로컬 로그온 허용](https://technet.microsoft.com/library/cc756809\(v=WS.10\).aspx)(영문)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50684-117">For more information, see [Allow log on locally](https://technet.microsoft.com/library/cc756809\(v=WS.10\).aspx).</span></span>

2.  <span data-ttu-id="50684-118">**일괄 작업으로 로그온**.</span><span class="sxs-lookup"><span data-stu-id="50684-118">**Log on as a batch job**.</span></span> <span data-ttu-id="50684-119">자세한 내용은 [일괄 작업으로 로그온](https://technet.microsoft.com/library/cc755659\(v=ws.10\).aspx)(영문)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50684-119">For more information, see [Log on as a batch job](https://technet.microsoft.com/library/cc755659\(v=ws.10\).aspx).</span></span>

3.  <span data-ttu-id="50684-120">정책에 대한 일반적인 정보는 [그룹 정책 개체의 보안 설정 편집](https://technet.microsoft.com/library/cc736516\(v=ws.10\).aspx)(영문)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50684-120">For general information on policies, see [Edit security settings on a Group Policy object](https://technet.microsoft.com/library/cc736516\(v=ws.10\).aspx).</span></span>

##  <a name="configure-stored-credentials-for-a-report-specific-data-source-native-mode"></a><a name="bkmk_stored_credentials_data_source_native"></a> <span data-ttu-id="50684-121">보고서별 데이터 원본에 대해 저장된 자격 증명 구성(기본 모드)</span><span class="sxs-lookup"><span data-stu-id="50684-121">Configure stored credentials for a report-specific data source (Native mode)</span></span>

1.  <span data-ttu-id="50684-122">기본 모드 보고서 관리자에서 보고서가 들어 있는 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="50684-122">In Native mode Report Manager, browse to the folder that contains the report.</span></span> <span data-ttu-id="50684-123">![Ssrs 항목에 대해 보고서 관리자에서](../media/ssrs-report-manager-item-context-menu.png "SSRS용 보고서 관리자의 상황에 맞는 메뉴 항목")항목 상황에 맞는 메뉴 상황에 맞는 메뉴를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-123">Click the item context menu ![context menu in report manager for ssrs items](../media/ssrs-report-manager-item-context-menu.png "context menu in report manager for ssrs items").</span></span>

2.  <span data-ttu-id="50684-124">**관리** 를 클릭한 다음 **데이터 원본**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-124">Click **Manage** and then click **Data Sources**.</span></span>

3.  <span data-ttu-id="50684-125">**사용자 지정 데이터 원본**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-125">Select **A custom data source**.</span></span>

4.  <span data-ttu-id="50684-126">**데이터 원본 유형** 목록에서 데이터 원본의 데이터를 처리하는 데 사용할 데이터 처리 확장 프로그램을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-126">In the **Data Source Type** list, select the data processing extension that is used to process data from the data source.</span></span>

5.  <span data-ttu-id="50684-127">**연결 문자열**에는 보고서 서버가 데이터 원본에 연결 하는 데 사용 하는 연결 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-127">For **Connection String**, specify the connection string that the report server uses to connect to the data source.</span></span> <span data-ttu-id="50684-128">다음 예에서는 데이터베이스에 연결 하는 데 사용 되는 연결 문자열을 보여 줍니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="50684-128">The following example illustrates a connection string used to connect to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database:</span></span>

    ```
    data source=<servername>;initial catalog=AdventureWorks2012
    ```

6.  <span data-ttu-id="50684-129">**연결 방법**으로 **보고서 서버에 안전하게 저장된 자격 증명**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-129">For **Connect Using**, select **Credentials stored securely in the report server**.</span></span>

7.  <span data-ttu-id="50684-130">사용자 이름 및 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-130">Type a user name and password.</span></span>

    -   <span data-ttu-id="50684-131">계정이 Windows 도메인 사용자 계정인 경우<계정 형식으로 지정한 \<domain> \\ \> 다음 **데이터 원본에 연결할 때 Windows 자격 증명으로 사용을 선택 합니다.**</span><span class="sxs-lookup"><span data-stu-id="50684-131">If the account is a Windows domain user account, specify it in this format: \<domain>\\<account\>, and then select **Use as Windows credentials when connecting to the data source.**</span></span>

    -   <span data-ttu-id="50684-132">사용자 이름과 암호가 데이터베이스 자격 증명인 경우 **데이터 원본에 연결할 때 Windows 자격 증명으로 사용**을 선택하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50684-132">If the user name and password are database credentials, do not select **Use as Windows credentials when connecting to the data source**.</span></span> <span data-ttu-id="50684-133">데이터베이스 서버가 가장 또는 위임을 지원하는 경우에는 **데이터 원본에 연결한 후 인증된 사용자로 가장**을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50684-133">If the database server supports impersonation or delegation, you can select **Impersonate the authenticated user after a connection has been made to the data source**.</span></span>

8.  <span data-ttu-id="50684-134">**적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-134">Click **Apply**.</span></span>

     <span data-ttu-id="50684-135">![맨 위 링크와 함께 사용되는 화살표 아이콘](../../2014-toc/media/uparrow16x16.gif "맨 위로 이동 링크와 함께 사용되는 화살표 아이콘") [저장된 자격 증명에 대한 보안 정책 요구 사항](#bkmk_top)</span><span class="sxs-lookup"><span data-stu-id="50684-135">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Security policy requirements for stored credentials](#bkmk_top)</span></span>

##  <a name="configure-stored-credentials-for-a-report-specific-data-source-sharepoint-mode"></a><a name="bkmk_stored_credentials_data_source_sharepoint"></a> <span data-ttu-id="50684-136">보고서별 데이터 원본에 대해 저장된 자격 증명 구성(SharePoint 모드)</span><span class="sxs-lookup"><span data-stu-id="50684-136">Configure stored credentials for a report-specific data source (SharePoint mode)</span></span>

1.  <span data-ttu-id="50684-137">보고서가 들어 있는 문서 라이브러리로 이동한 다음, 열기 메뉴 ![SSRS의 문서 라이브러리 상황에 맞는 메뉴 항목](../media/ssrs-sharepoint-item-context-menu.png "SSRS의 문서 라이브러리 상황에 맞는 메뉴 항목")을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-137">Browse to the document library that contains the report and then click the open menu ![document library context menu for ssrs items](../media/ssrs-sharepoint-item-context-menu.png "document library context menu for ssrs items").</span></span>

2.  <span data-ttu-id="50684-138">두 번째 열기 메뉴 ![SSRS의 문서 라이브러리 상황에 맞는 메뉴 항목](../media/ssrs-sharepoint-item-context-menu.png "SSRS의 문서 라이브러리 상황에 맞는 메뉴 항목") 및 **데이터 원본 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-138">Click second open menu ![document library context menu for ssrs items](../media/ssrs-sharepoint-item-context-menu.png "document library context menu for ssrs items") and then click **Manage Data Sources**.</span></span>

3.  <span data-ttu-id="50684-139">저장된 자격 증명으로 구성할 **사용자 지정** 데이터 원본의 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-139">Click the name of the **Custom** data source you want to configure with stored credentials.</span></span>

4.  <span data-ttu-id="50684-140">**데이터 원본 유형** 목록에서 데이터 원본의 데이터를 처리하는 데 사용할 데이터 처리 확장 프로그램을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-140">In the **Data Source Type** list, select the data processing extension that is used to process data from the data source.</span></span>

5.  <span data-ttu-id="50684-141">**연결 문자열**에는 보고서 서버가 데이터 원본에 연결 하는 데 사용 하는 연결 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-141">For **Connection String**, specify the connection string that the report server uses to connect to the data source.</span></span> <span data-ttu-id="50684-142">다음 예에서는 데이터베이스에 연결 하는 데 사용 되는 연결 문자열을 보여 줍니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="50684-142">The following example illustrates a connection string used to connect to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database:</span></span>

    ```
    data source=<servername>;initial catalog=AdventureWorks2012
    ```

6.  <span data-ttu-id="50684-143">**자격 증명**에 대해 **저장된 자격 증명**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-143">For **Credentials**, select **Stored Credentials**.</span></span>

7.  <span data-ttu-id="50684-144">**사용자 이름** 및 **암호**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-144">Type a **user name** and **password**.</span></span>

    -   <span data-ttu-id="50684-145">계정이 Windows 도메인 사용자 계정인 경우<계정 형식으로 지정한 \<domain> \\ \> 다음 **데이터 원본에 연결할 때 Windows 자격 증명으로 사용을 선택 합니다.**</span><span class="sxs-lookup"><span data-stu-id="50684-145">If the account is a Windows domain user account, specify it in this format: \<domain>\\<account\>, and then select **Use as Windows credentials when connecting to the data source.**</span></span>

    -   <span data-ttu-id="50684-146">사용자 이름과 암호가 데이터베이스 자격 증명인 경우 **Windows 자격 증명으로 사용**을 선택하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50684-146">If the user name and password are database credentials, do not select **Use as Windows credentials**.</span></span> <span data-ttu-id="50684-147">데이터베이스 서버가 가장 또는 위임을 지 원하는 경우 **실행 컨텍스트를이 계정으로 설정**을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50684-147">If the database server supports impersonation or delegation, you can select **Set execution context to this account**.</span></span>

8.  <span data-ttu-id="50684-148">**OK**(확인)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-148">Click **ok**.</span></span>

     <span data-ttu-id="50684-149">![맨 위 링크와 함께 사용되는 화살표 아이콘](../../2014-toc/media/uparrow16x16.gif "맨 위로 이동 링크와 함께 사용되는 화살표 아이콘") [저장된 자격 증명에 대한 보안 정책 요구 사항](#bkmk_top)</span><span class="sxs-lookup"><span data-stu-id="50684-149">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Security policy requirements for stored credentials](#bkmk_top)</span></span>

##  <a name="configure-stored-credentials-for-a-shared-data-source-native-mode"></a><a name="bkmk_stored_credentials_shared_data_source_native"></a> <span data-ttu-id="50684-150">공유 데이터 원본에 대해 저장된 자격 증명 구성(기본 모드)</span><span class="sxs-lookup"><span data-stu-id="50684-150">Configure stored credentials for a shared data source (Native mode)</span></span>

1.  <span data-ttu-id="50684-151">기본 모드 보고서 관리자에서 공유 데이터 원본 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="50684-151">In Native mode Report Manager, browse to the shared data source item.</span></span> <span data-ttu-id="50684-152">![공유 데이터 원본 아이콘](../media/hlp-16datasource.png "공유 데이터 원본 아이콘")</span><span class="sxs-lookup"><span data-stu-id="50684-152">![Shared data source icon](../media/hlp-16datasource.png "Shared data source icon")</span></span>

2.  <span data-ttu-id="50684-153">![보고서 관리자에서 ssrs 항목에 대 한 상황에](../media/ssrs-report-manager-item-context-menu.png "SSRS용 보고서 관리자의 상황에 맞는 메뉴 항목") 맞는 메뉴 상황에 맞는 메뉴를 클릭 한 다음 **관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-153">Click the context menu ![context menu in report manager for ssrs items](../media/ssrs-report-manager-item-context-menu.png "context menu in report manager for ssrs items") and then click **Manage**.</span></span>

3.  <span data-ttu-id="50684-154">데이터 **원본 유형** 목록에서 데이터 원본의 데이터를 처리 하는 데 사용 되는 데이터 처리 확장 프로그램을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-154">In the **Data Source Type** list, specify the data processing extension that is used to process data from the data source.</span></span>

4.  <span data-ttu-id="50684-155">**연결 문자열**에는 보고서 서버가 데이터 원본에 연결 하는 데 사용 하는 연결 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-155">For **Connection String**, specify the connection string that the report server uses to connect to the data source.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="50684-156">에서는 연결 문자열에서 자격 증명을 지정하지 않는 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-156">recommends that you do not specify credentials in the connection string.</span></span>

     <span data-ttu-id="50684-157">다음 예에서는 로컬 데이터베이스에 연결 하는 데 사용 되는 연결 문자열을 보여 줍니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="50684-157">The following example illustrates a connection string used to connect to the local [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database:</span></span>

    ```
    data source=<localservername>; initial catalog=AdventureWorks2012
    ```

5.  <span data-ttu-id="50684-158">사용자 이름 및 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-158">Type a user name and password.</span></span>

    -   <span data-ttu-id="50684-159">계정이 Windows 도메인 사용자 계정인 경우<계정 형식으로 지정한 \<domain> \\ \> 다음 **데이터 원본에 연결할 때 Windows 자격 증명으로 사용을 선택 합니다.**</span><span class="sxs-lookup"><span data-stu-id="50684-159">If the account is a Windows domain user account, specify it in this format: \<domain>\\<account\>, and then select **Use as Windows credentials when connecting to the data source.**</span></span>

    -   <span data-ttu-id="50684-160">사용자 이름과 암호가 데이터베이스 자격 증명인 경우 **데이터 원본에 연결할 때 Windows 자격 증명으로 사용**을 선택하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50684-160">If the user name and password are database credentials, do not select **Use as Windows credentials when connecting to the data source**.</span></span> <span data-ttu-id="50684-161">데이터베이스 서버가 가장 또는 위임을 지원하는 경우에는 **데이터 원본에 연결한 후 인증된 사용자로 가장**을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50684-161">If the database server supports impersonation or delegation, you can select **Impersonate the authenticated user after a connection has been made to the data source**.</span></span>

6.  <span data-ttu-id="50684-162">**적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-162">Click **Apply**.</span></span>

     <span data-ttu-id="50684-163">![맨 위 링크와 함께 사용되는 화살표 아이콘](../../2014-toc/media/uparrow16x16.gif "맨 위로 이동 링크와 함께 사용되는 화살표 아이콘") [저장된 자격 증명에 대한 보안 정책 요구 사항](#bkmk_top)</span><span class="sxs-lookup"><span data-stu-id="50684-163">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Security policy requirements for stored credentials](#bkmk_top)</span></span>

##  <a name="configure-stored-credentials-for-a-shared-data-source-sharepoint-mode"></a><a name="bkmk_stored_credentials_shared_data_source_sharepoint"></a><span data-ttu-id="50684-164">공유 데이터 원본에 대 한 저장 된 자격 증명 구성 (SharePoint 모드)</span><span class="sxs-lookup"><span data-stu-id="50684-164">Configure stored credentials for a shared data source (SharePoint mode)</span></span>

1.  <span data-ttu-id="50684-165">문서 라이브러리에서 공유 데이터 원본 항목을 찾습니다.![공유 데이터 원본 아이콘](../media/hlp-16datasource.png "공유 데이터 원본 아이콘")</span><span class="sxs-lookup"><span data-stu-id="50684-165">In the document library, browse to the shared data source item.![Shared data source icon](../media/hlp-16datasource.png "Shared data source icon")</span></span>

2.  <span data-ttu-id="50684-166">바로 가기 메뉴인 ![SSRS의 문서 라이브러리 상황에 맞는 메뉴 항목](../media/ssrs-sharepoint-item-context-menu.png "SSRS의 문서 라이브러리 상황에 맞는 메뉴 항목")을 클릭한 다음, 두 번째 바로 가기 메뉴인 ![SSRS의 문서 라이브러리 상황에 맞는 메뉴 항목](../media/ssrs-sharepoint-item-context-menu.png "SSRS의 문서 라이브러리 상황에 맞는 메뉴 항목")을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-166">Click the context menu ![document library context menu for ssrs items](../media/ssrs-sharepoint-item-context-menu.png "document library context menu for ssrs items") and then click the second context menu ![document library context menu for ssrs items](../media/ssrs-sharepoint-item-context-menu.png "document library context menu for ssrs items").</span></span>

3.  <span data-ttu-id="50684-167">**데이터 원본 정의 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-167">Click **Edit Data Source Definition**.</span></span>

4.  <span data-ttu-id="50684-168">데이터 **원본 유형** 목록에서 데이터 원본의 데이터를 처리 하는 데 사용 되는 데이터 처리 확장 프로그램을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-168">In the **Data Source Type** list, specify the data processing extension that is used to process data from the data source.</span></span>

5.  <span data-ttu-id="50684-169">**연결 문자열**에는 보고서 서버가 데이터 원본에 연결 하는 데 사용 하는 연결 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-169">For **Connection String**, specify the connection string that the report server uses to connect to the data source.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="50684-170">에서는 연결 문자열에서 자격 증명을 지정하지 않는 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-170">recommends that you do not specify credentials in the connection string.</span></span>

     <span data-ttu-id="50684-171">다음 예에서는 로컬 데이터베이스에 연결 하는 데 사용 되는 연결 문자열을 보여 줍니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="50684-171">The following example illustrates a connection string used to connect to the local [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database:</span></span>

    ```
    data source=<localservername>; initial catalog=AdventureWorks2012
    ```

6.  <span data-ttu-id="50684-172">사용자 이름 및 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-172">Type a user name and password.</span></span>

    -   <span data-ttu-id="50684-173">계정이 Windows 도메인 사용자 계정인 경우<계정 형식으로 지정한 \<domain> \\ \> 다음 **Windows 자격 증명으로 사용을 선택 합니다.**</span><span class="sxs-lookup"><span data-stu-id="50684-173">If the account is a Windows domain user account, specify it in this format: \<domain>\\<account\>, and then select **Use as Windows credentials.**</span></span>

    -   <span data-ttu-id="50684-174">사용자 이름과 암호가 데이터베이스 자격 증명인 경우 **Windows 자격 증명으로 사용**을 선택하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50684-174">If the user name and password are database credentials, do not select **Use as Windows credentials**.</span></span> <span data-ttu-id="50684-175">데이터베이스 서버에서 가장 또는 위임이 지원되는 경우 **실행 컨텍스트를 이 계정으로 설정**을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50684-175">If the database server supports impersonation or delegation, you can select **Set Execution context to this account**.</span></span>

7.  <span data-ttu-id="50684-176">**Ok**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50684-176">Click **Ok**.</span></span>

     <span data-ttu-id="50684-177">![맨 위 링크와 함께 사용되는 화살표 아이콘](../../2014-toc/media/uparrow16x16.gif "맨 위로 이동 링크와 함께 사용되는 화살표 아이콘") [저장된 자격 증명에 대한 보안 정책 요구 사항](#bkmk_top)</span><span class="sxs-lookup"><span data-stu-id="50684-177">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Security policy requirements for stored credentials](#bkmk_top)</span></span>

## <a name="see-also"></a><span data-ttu-id="50684-178">참고 항목</span><span class="sxs-lookup"><span data-stu-id="50684-178">See Also</span></span>
 <span data-ttu-id="50684-179">[보고서 데이터 원본에 대 한 자격 증명 및 연결 정보 지정](../../integration-services/connection-manager/data-sources.md) 보고서에 대 한 [데이터 원본 속성 구성 &#40;보고서 관리자&#41;](configure-data-source-properties-for-a-report-report-manager.md) 보고서 관리자&#41;[데이터 원본 속성 페이지](../data-sources-properties-page-report-manager.md) [를 만들거나 삭제 하거나 수정할 &#40;](../create-delete-or-modify-a-shared-data-source-report-manager.md) &#40;보고서 관리자 [새 데이터 원본 페이지](../new-data-source-page-report-manager.md)&#41;&#40;</span><span class="sxs-lookup"><span data-stu-id="50684-179">[Specify Credential and Connection Information for Report Data Sources](../../integration-services/connection-manager/data-sources.md) [Configure Data Source Properties for a Report  &#40;Report Manager&#41;](configure-data-source-properties-for-a-report-report-manager.md) [Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) [Data Sources Properties Page &#40;Report Manager&#41;](../data-sources-properties-page-report-manager.md) [New Data Source Page &#40;Report Manager&#41;](../new-data-source-page-report-manager.md)</span></span>



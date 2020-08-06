---
title: SharePoint 사이트의 보고서 데이터 원본에서 자격 증명 업데이트 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e0c50b6e-89e7-4b4d-8fe5-c90682c5d1b1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 923fee5656ed6032201fb4276fcca75be799e42d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639319"
---
# <a name="update-credentials-in-report-data-sources-from-a-sharepoint-site"></a><span data-ttu-id="cf5ab-102">SharePoint 사이트의 보고서 데이터 원본에서 자격 증명 업데이트</span><span class="sxs-lookup"><span data-stu-id="cf5ab-102">Update Credentials in Report Data Sources from a SharePoint Site</span></span>
  <span data-ttu-id="cf5ab-103">이 항목에서는 SharePoint 문서 라이브러리에 저장된 공유 데이터 원본 및 보고서에 포함된 데이터 원본을 업데이트하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-103">This topic describes how to update data sources embedded in reports and shared data sources that are saved in a SharePoint document library.</span></span>  
  
 <span data-ttu-id="cf5ab-104">보고서 중 상당수에 데이터 원본이 포함되어 있거나 Windows 인증을 사용하도록 구성된 공유 데이터 원본이 사용되고 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-104">Many of your reports might include data sources or use shared data sources that are configured to use Windows Authentication.</span></span> <span data-ttu-id="cf5ab-105">SharePoint 문서 라이브러리에 저장된 보고서에 대해 데이터 경고를 만드는 것과 같은 일부 상황에서는 데이터 원본 자격 증명을 저장된 자격 증명으로 업데이트하거나 자격 증명을 필요로 하지 않도록 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-105">Under some circumstances, such as creating data alerts on reports saved to a SharePoint document library, you need to update the data source credentials to stored credentials or require no credentials.</span></span>  
  
 <span data-ttu-id="cf5ab-106">보고서에서 저장된 자격 증명을 사용하기 위해 새 SQL Server 로그인을 만들어 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-106">To use stored credentials in reports, you might decide to create and use a new SQL Server login.</span></span> <span data-ttu-id="cf5ab-107">자세한 내용은 [로그인 만들기](../../relational-databases/security/authentication-access/create-a-login.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-107">For more information, see [Create a Login](../../relational-databases/security/authentication-access/create-a-login.md).</span></span>  
  
### <a name="to-update-an-embedded-data-source-to-use-stored-credentials"></a><span data-ttu-id="cf5ab-108">저장된 자격 증명을 사용하도록 포함된 데이터 원본을 업데이트하려면</span><span class="sxs-lookup"><span data-stu-id="cf5ab-108">To update an embedded data source to use stored credentials</span></span>  
  
1.  <span data-ttu-id="cf5ab-109">보고서를 저장한 SharePoint 문서 라이브러리로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-109">Go to the SharePoint document library where you saved the report.</span></span>  
  
2.  <span data-ttu-id="cf5ab-110">보고서에서 확장 드롭다운 메뉴 아이콘을 클릭한 다음 **데이터 원본 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-110">Click the icon for the expand drop-down menu on the report and then click **Manage Data Sources**.</span></span>  
  
     <span data-ttu-id="cf5ab-111">데이터 원본 관리 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-111">The Manage Data Sources page opens.</span></span>  
  
3.  <span data-ttu-id="cf5ab-112">**이름** 열에서 데이터 원본을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-112">In the **Name** column, click the data source.</span></span>  
  
4.  <span data-ttu-id="cf5ab-113">**연결 형식** 에 대해 **사용자 지정 데이터 원본** 옵션이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-113">For **Connection Type** verify that the **Custom data source** option is selected.</span></span>  
  
     <span data-ttu-id="cf5ab-114">이 옵션은 데이터 원본이 보고서에 포함됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-114">This option indicates that the data source is embedded in the report.</span></span>  
  
5.  <span data-ttu-id="cf5ab-115">보고서를 다른 데이터 원본 유형, 다른 서버 또는 데이터 저장소에 연결하려는 것이 아닌 한 **데이터 원본 유형** 및 **연결 문자열** 옵션을 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-115">Leave the **Data Source Type** and **Connection string** options as they are, unless you want the report to connect to different type of data source, a different server, or data store.</span></span>  
  
6.  <span data-ttu-id="cf5ab-116">**자격 증명**에 대해 **저장된 자격 증명**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-116">For **Credentials**, select **Stored credentials**.</span></span> <span data-ttu-id="cf5ab-117">이 옵션은 데이터 원본이 자격 증명을 허용하지 않거나 사용자가 다른 방법으로 자격 증명을 전달하는 경우에만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-117">This option works only if the data source does not accept credentials or if you are passing credentials some other way.</span></span>  
  
     <span data-ttu-id="cf5ab-118">일부 상황에서는 **자격 증명 필요 없음** 옵션을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-118">The **Credentials are not required** option can also be used under some circumstances.</span></span>  
  
     <span data-ttu-id="cf5ab-119">일부 데이터 원본 유형의 경우 보고서 서버에서 무인 실행 계정을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-119">From some data source types, the unattended execution account must be configured on the report server.</span></span> <span data-ttu-id="cf5ab-120">자세한 내용은 [외부 데이터 원본의 데이터 추가&#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md) 및 [무인 실행 계정 구성&#40;SSRS 구성 관리자&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)의 해당하는 데이터 원본 유형에 대한 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-120">For more information, see the topic for the corresponding data source type in [Add Data from External Data Sources &#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md) and [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).</span></span>  
  
7.  <span data-ttu-id="cf5ab-121">사용자 이름 및 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-121">Type a user name and password.</span></span>  
  
    -   <span data-ttu-id="cf5ab-122">계정이 Windows 도메인 사용자 계정인 경우<계정 형식으로 지정한 \<domain> \\ \> 다음 **데이터 원본에 연결할 때 Windows 자격 증명으로 사용**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-122">If the account is a Windows domain user account, specify it in this format: \<domain>\\<account\>, and then select **Use as Windows credentials when connecting to the data source**.</span></span>  
  
    -   <span data-ttu-id="cf5ab-123">사용자 이름과 암호가 데이터베이스 자격 증명인 경우 **데이터 원본에 연결할 때 Windows 자격 증명으로 사용**을 선택하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-123">If the user name and password are database credentials, do not select **Use as Windows credentials when connecting to the data source**.</span></span> <span data-ttu-id="cf5ab-124">데이터베이스 서버에서 가장 또는 위임이 지원되는 경우 **실행 컨텍스트를 이 계정으로 설정**을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-124">If the database server supports impersonation or delegation, you can select **Set execution context to this account**.</span></span>  
  
8.  <span data-ttu-id="cf5ab-125">업데이트된 자격 증명을 사용하여 데이터 원본 연결을 확인하려면 **연결 테스트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-125">To verify the data source can connect by using the updated credentials, click **Test connection**.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-update-a-shared-data-source-to-use-stored-credentials"></a><span data-ttu-id="cf5ab-126">저장된 자격 증명을 사용하도록 공유 데이터 원본을 업데이트하려면</span><span class="sxs-lookup"><span data-stu-id="cf5ab-126">To update a shared data source to use stored credentials</span></span>  
  
1.  <span data-ttu-id="cf5ab-127">공유 데이터 원본을 저장한 SharePoint 문서 라이브러리로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-127">Go to the SharePoint document library where you saved the shared data source.</span></span>  
  
2.  <span data-ttu-id="cf5ab-128">공유 데이터 원본에서 확장 드롭다운 메뉴 아이콘을 클릭한 다음 **데이터 원본 정의 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-128">Click the icon for the expand drop-down menu on shared data source, and then click **Edit Data Source Definition**.</span></span>  
  
     <span data-ttu-id="cf5ab-129">데이터 원본 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-129">The Data Source page opens.</span></span>  
  
3.  <span data-ttu-id="cf5ab-130">공유 데이터 원본을 다른 데이터 원본 유형, 다른 서버 또는 데이터 저장소에 연결하려는 것이 아닌 한 **데이터 원본 유형** 및 **연결 문자열** 옵션을 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-130">Leave the **Data Source Type** and **Connection string** options as they are, unless you want the shared data source to connect to different type of data source, a different server, or data store.</span></span>  
  
4.  <span data-ttu-id="cf5ab-131">**자격 증명**에 대해 **저장된 자격 증명**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-131">For **Credentials**, select **Stored credentials**.</span></span>  
  
     <span data-ttu-id="cf5ab-132">일부 상황에서는 **자격 증명 필요 없음** 옵션을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-132">The **Credentials are not required** option can also be used under some circumstances.</span></span> <span data-ttu-id="cf5ab-133">이 옵션은 데이터 원본이 자격 증명을 허용하지 않거나 사용자가 다른 방법으로 자격 증명을 전달하는 경우에만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-133">This option works only if the data source does not accept credentials or if you are passing credentials some other way.</span></span>  
  
     <span data-ttu-id="cf5ab-134">일부 데이터 원본 유형의 경우 보고서 서버에서 무인 실행 계정을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-134">From some data source types, the unattended execution account must be configured on the report server.</span></span> <span data-ttu-id="cf5ab-135">자세한 내용은 [외부 데이터 원본의 데이터 추가&#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md) 및 [무인 실행 계정 구성&#40;SSRS 구성 관리자&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)의 해당하는 데이터 원본 유형에 대한 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-135">For more information, see the topic for the corresponding data source type in [Add Data from External Data Sources &#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md) and [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).</span></span>  
  
5.  <span data-ttu-id="cf5ab-136">사용자 이름 및 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-136">Type a user name and password.</span></span>  
  
    -   <span data-ttu-id="cf5ab-137">계정이 Windows 도메인 사용자 계정인 경우<계정 형식으로 지정한 \<domain> \\ \> 다음 **데이터 원본에 연결할 때 Windows 자격 증명으로 사용을 선택 합니다.**</span><span class="sxs-lookup"><span data-stu-id="cf5ab-137">If the account is a Windows domain user account, specify it in this format: \<domain>\\<account\>, and then select **Use as Windows credentials when connecting to the data source.**</span></span>  
  
    -   <span data-ttu-id="cf5ab-138">사용자 이름과 암호가 데이터베이스 자격 증명인 경우 **데이터 원본에 연결할 때 Windows 자격 증명으로 사용**을 선택하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-138">If the user name and password are database credentials, do not select **Use as Windows credentials when connecting to the data source**.</span></span> <span data-ttu-id="cf5ab-139">데이터베이스 서버에서 가장 또는 위임이 지원되는 경우 **실행 컨텍스트를 이 계정으로 설정**을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-139">If the database server supports impersonation or delegation, you can select **Set execution context to this account**.</span></span>  
  
6.  <span data-ttu-id="cf5ab-140">업데이트된 자격 증명을 사용하여 데이터 원본 연결을 확인하려면 **연결 테스트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-140">To verify the data source can connect using the updated credentials, **Test connection**.</span></span>  
  
7.  <span data-ttu-id="cf5ab-141">이 데이터 원본 사용이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="cf5ab-141">Verify that Enable this data source is selected.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cf5ab-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cf5ab-142">See Also</span></span>  
 [<span data-ttu-id="cf5ab-143">SharePoint 라이브러리에 문서 업로드&#40;SharePoint 모드의 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="cf5ab-143">Upload Documents to a SharePoint Library &#40;Reporting Services in SharePoint Mode&#41;</span></span>](../upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md)  
  
  

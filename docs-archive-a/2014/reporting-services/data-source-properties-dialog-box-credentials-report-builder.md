---
title: 데이터 원본 속성 대화 상자, 자격 증명 (보고서 작성기) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10017"
ms.assetid: 4531f09f-d653-4c05-a120-d7788838bc99
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9e47ba571e2b0adf2738499c1d027a4edde86e3f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652633"
---
# <a name="data-source-properties-dialog-box-credentials-report-builder"></a><span data-ttu-id="2e7ef-102">데이터 원본 속성 대화 상자, 자격 증명(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="2e7ef-102">Data Source Properties Dialog Box, Credentials (Report Builder)</span></span>
  <span data-ttu-id="2e7ef-103">**데이터 원본 속성** 대화 상자에서 **자격 증명** 을 선택하여 보고서의 포함된 데이터 원본에 연결하는 데 사용할 자격 증명을 표시하고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e7ef-103">Select **Credentials** on the **Data Source Properties** dialog box to display and modify credentials to connect to an embedded data source in the report.</span></span> <span data-ttu-id="2e7ef-104">사용자가 제공하는 자격 증명은 데이터 원본에 액세스하여 보고서를 미리 보는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e7ef-104">The credentials that you provide are used to access the data source for previewing reports.</span></span> <span data-ttu-id="2e7ef-105">자격 증명에 대한 자세한 내용은 [보고서 작성기에 자격 증명 지정](../../2014/reporting-services/specify-credentials-in-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2e7ef-105">For more information about credentials, see [Specify Credentials in Report Builder](../../2014/reporting-services/specify-credentials-in-report-builder.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="2e7ef-106">옵션</span><span class="sxs-lookup"><span data-stu-id="2e7ef-106">Options</span></span>  
 <span data-ttu-id="2e7ef-107">**Windows 인증 사용(통합 보안)**</span><span class="sxs-lookup"><span data-stu-id="2e7ef-107">**Use Windows Authentication (integrated security)**</span></span>  
 <span data-ttu-id="2e7ef-108">Windows 인증을 사용하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7ef-108">Select this option to use Windows Authentication.</span></span>  
  
 <span data-ttu-id="2e7ef-109">**이 사용자 이름 및 암호 사용**</span><span class="sxs-lookup"><span data-stu-id="2e7ef-109">**Use this user name and password**</span></span>  
 <span data-ttu-id="2e7ef-110">특정 사용자 이름 및 암호를 제공하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7ef-110">Select this option to provide a specific user name and password.</span></span> <span data-ttu-id="2e7ef-111">포함된 데이터 원본의 경우 보고서 서버 프로젝트를 대상 서버에 게시하면 사용자 이름과 암호가 데이터베이스에 대해 저장된 자격 증명으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e7ef-111">For embedded data sources: when you publish the report server project to the target server, the user name and password are saved as the stored credentials for the database.</span></span> <span data-ttu-id="2e7ef-112">사용자 이름과 암호를 Windows 자격 증명으로 사용하려는 경우 대상 서버에서 게시된 공유 데이터 원본에 대한 속성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e7ef-112">If you want to use the user name and password as Windows credentials, you can change the properties for the published shared data source on the target server.</span></span> <span data-ttu-id="2e7ef-113">자세한 내용은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [온라인 설명서](https://go.microsoft.com/fwlink/?linkid=121312)의 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 설명서에서 [공유 데이터 원본 만들기, 삭제 또는 수정&#40;보고서 관리자&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2e7ef-113">For more information, see [Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md) in the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
 <span data-ttu-id="2e7ef-114">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="2e7ef-114">**User name**</span></span>  
 <span data-ttu-id="2e7ef-115">데이터 원본에 로그온할 때 사용할 사용자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7ef-115">Type a user name to log on to the data source.</span></span>  
  
 <span data-ttu-id="2e7ef-116">**암호**</span><span class="sxs-lookup"><span data-stu-id="2e7ef-116">**Password**</span></span>  
 <span data-ttu-id="2e7ef-117">데이터 원본에 로그온할 때 사용할 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7ef-117">Type a password to log on to the data source.</span></span>  
  
 <span data-ttu-id="2e7ef-118">**자격 증명 확인**</span><span class="sxs-lookup"><span data-stu-id="2e7ef-118">**Prompt for credentials**</span></span>  
 <span data-ttu-id="2e7ef-119">보고서 실행 시 자격 증명을 요청하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7ef-119">Select this option to prompt for credentials when the report runs.</span></span>  
  
 <span data-ttu-id="2e7ef-120">**프롬프트 문자열 입력**</span><span class="sxs-lookup"><span data-stu-id="2e7ef-120">**Enter prompt string**</span></span>  
 <span data-ttu-id="2e7ef-121">데이터 원본에 대한 로그인 자격 증명을 제공하도록 사용자에게 표시할 메시지를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7ef-121">Type a sentence to instruct the user to provide login credentials for the data source.</span></span>  
  
 <span data-ttu-id="2e7ef-122">**자격 증명 없음**</span><span class="sxs-lookup"><span data-stu-id="2e7ef-122">**No credentials**</span></span>  
 <span data-ttu-id="2e7ef-123">데이터 원본에 대해 자격 증명을 사용하지 않으려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7ef-123">Select this option to provide no credentials for the data source.</span></span> <span data-ttu-id="2e7ef-124">이 옵션은 데이터 원본이 자격 증명을 허용하지 않거나 다른 방법으로 자격 증명을 전달하는 경우에만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7ef-124">This option only works if the data source does not accept credentials or if you are passing credentials some other way.</span></span>  
  
 <span data-ttu-id="2e7ef-125">일부 데이터 확장 프로그램의 경우 보고서 서버에 무인 실행 계정을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7ef-125">From some data extensions, the unattended execution account must be configured on the report server.</span></span>  
  
 <span data-ttu-id="2e7ef-126">자세한 내용은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [온라인 설명서](https://go.microsoft.com/fwlink/?linkid=121312)의 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 설명서에서 [외부 데이터 원본의 데이터 추가&#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md) 및 [무인 실행 계정 구성&#40;SSRS 구성 관리자&#41;](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)의 해당하는 데이터 원본 유형에 대한 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2e7ef-126">For more information, see the topic for the corresponding data source type in [Add Data from External Data Sources &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md) and [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) in the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e7ef-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2e7ef-127">See Also</span></span>  
 <span data-ttu-id="2e7ef-128">[대화 상자, 창 및 마법사에 대 한 보고서 작성기 도움말](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="2e7ef-128">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="2e7ef-129">[데이터 원본 속성 대화 상자, 일반 &#40;보고서 작성기&#41;](../../2014/reporting-services/data-source-properties-dialog-box-general-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="2e7ef-129">[Data Source Properties Dialog Box, General &#40;Report Builder&#41;](../../2014/reporting-services/data-source-properties-dialog-box-general-report-builder.md) </span></span>  
 <span data-ttu-id="2e7ef-130">[데이터 연결이 나 데이터 원본 &#40;보고서 작성기 및 SSRS를 추가 하 고 확인&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2e7ef-130">[Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="2e7ef-131">보고서 &#40;보고서 작성기 및 SSRS&#41;에 데이터를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7ef-131">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-data/report-datasets-ssrs.md)  
  
  

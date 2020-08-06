---
title: 데이터 원본 속성 대화 상자, 일반 (보고서 작성기) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10018"
ms.assetid: b956f43a-8426-4679-acc1-00f405d5ff5b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dcfba8346a3519817a36c21b24be1a91a613e098
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639412"
---
# <a name="data-source-properties-dialog-box-general-report-builder"></a><span data-ttu-id="00677-102">데이터 원본 속성 대화 상자, 일반(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="00677-102">Data Source Properties Dialog Box, General (Report Builder)</span></span>
  <span data-ttu-id="00677-103">**데이터 원본 속성** 대화 상자에서 **일반** 을 선택하여 보고서 서버의 공유 데이터 원본을 선택하거나 보고서에 포함된 데이터 원본에 대한 연결 정보를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00677-103">Select **General** on the **Data Source Properties** dialog box to select a shared data source from a report server or to create or modify connection information for a data source embedded in the report.</span></span>  
  
 <span data-ttu-id="00677-104">데이터 원본을 연결하는 데 사용되는 자격 증명 유형은 데이터 원본 속성에서 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="00677-104">The type of credentials used to connect to a data source is specified in the data source properties.</span></span> <span data-ttu-id="00677-105">보고서 서버에서 보고서를 열면 데이터 원본 속성에 지정된 런타임 자격 증명이 쿼리를 만들고 보고서를 미리 보는 등의 디자인 타임 태스크에 대해 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00677-105">When you open a report from the report server, the run-time credentials, specified in the data source properties, might not work for design time tasks such as creating queries and previewing reports.</span></span> <span data-ttu-id="00677-106">예를 들어 데이터 원본에서 사용자 이름 및 암호 이외에 사용자가 모르는 Windows 자격 증명을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00677-106">For example, the data source might use Windows credentials other than yours or a user name and password that are unknown to you.</span></span>  
  
 <span data-ttu-id="00677-107">보고서 작성기에서는 데이터 원본 속성에 제공된 자격 증명을 사용하여 데이터 원본에 연결할 수 없는 경우 **데이터 원본 자격 증명 입력** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="00677-107">Report Builder opens the **Enter Data Source Credentials** dialog box when it is unable to connect to the data source using the credentials provided in the data source properties.</span></span> <span data-ttu-id="00677-108">일반적으로 이 오류는 다음과 같은 경우에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="00677-108">Typically this happens when:</span></span>  
  
-   <span data-ttu-id="00677-109">데이터 원본이 자격 증명을 요청하도록 구성된 경우</span><span class="sxs-lookup"><span data-stu-id="00677-109">The data source is configured to prompt for credentials.</span></span>  
  
-   <span data-ttu-id="00677-110">데이터 원본이 저장된 자격 증명을 사용하도록 구성된 경우</span><span class="sxs-lookup"><span data-stu-id="00677-110">The data source is configured to use stored credentials.</span></span>  <span data-ttu-id="00677-111">잠재적 보안 위협을 최소화하기 위해 보고서 작성기는 서버에 저장된 자격 증명을 검색하지 않도록 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="00677-111">To minimize potential security threats, Report Builder is designed to not retrieve credentials stored on the server.</span></span>  
  
 <span data-ttu-id="00677-112">**데이터 원본 자격 증명 입력** 대화 상자를 사용하여 디자인 타임에 보고서 작성기에서 현재 Windows 사용자로 데이터 원본에 연결하는 데 사용하는 자격 증명을 변경하거나 사용자 이름 및 암호를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00677-112">You can use the **Enter Data Source Credentials** dialog box to change the credentials used by Report Builder at design time to connect to the data source as the current Windows user or provide a user name and password.</span></span> <span data-ttu-id="00677-113">사용자 이름 및 암호를 제공할 경우 해당 사용자 이름 및 암호를 Windows 자격 증명으로 사용할지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00677-113">If you provide a user name and password you can indicate whether they are used as Windows credentials.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="00677-114">쿼리 디자이너에서는 디자인 타임 자격 증명에 대해 다른 자격 증명 유형을 지정할 수 있지만 보고서 미리 보기에서는 데이터 원본에 지정된 기존 자격 증명 옵션에 대한 사용자 이름 및 암호만 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00677-114">Although the query designers allow you to specify other another credentials type for design-time credentials, report preview only allows you to enter the user name and password for the existing credentials options specified in the data source.</span></span>  
  
 <span data-ttu-id="00677-115">**연결 테스트**를 클릭하면 데이터 원본 속성 자격 증명 페이지에 지정된 자격 증명을 사용하여 데이터 원본에 대한 연결이 테스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="00677-115">When you click **Test Connection**, the connection to the data source is tested using the credentials specified in the data source properties credentials page.</span></span> <span data-ttu-id="00677-116">포함된 데이터 원본 및 공유 데이터 원본에 대한 연결을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00677-116">You can test connections to embedded and shared data sources.</span></span>  
  
 <span data-ttu-id="00677-117">지정된 자격 증명이 완전하지 않으면(예: 암호가 필요한 경우) 데이터 원본에 연결해야 하는 경우 보고서 작성기에 런타임 자격 증명을 묻는 메시지가 다시 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="00677-117">If the credentials specified are incomplete (for example, a password is required), Report Builder prompts you again for run-time credentials when it needs to connect the data source.</span></span> <span data-ttu-id="00677-118">디자인 타임 자격 증명은 저장되므로 확인 메시지가 다시 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00677-118">The design-time credentials are stored and you are not prompted again.</span></span>  
  
## <a name="options"></a><span data-ttu-id="00677-119">옵션</span><span class="sxs-lookup"><span data-stu-id="00677-119">Options</span></span>  
 <span data-ttu-id="00677-120">**이름**</span><span class="sxs-lookup"><span data-stu-id="00677-120">**Name**</span></span>  
 <span data-ttu-id="00677-121">데이터 원본의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="00677-121">Type the name of the data source.</span></span> <span data-ttu-id="00677-122">데이터 원본 이름은 보고서 내에서 중복되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00677-122">The data source name must be unique within the report.</span></span> <span data-ttu-id="00677-123">기본적으로 DataSource1 또는 DataSource2 같은 일반 이름이 데이터 원본에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="00677-123">By default, a general name, such as DataSource1 or DataSource2, is assigned to the data source.</span></span>  
  
 <span data-ttu-id="00677-124">**공유 연결 사용**</span><span class="sxs-lookup"><span data-stu-id="00677-124">**Use a shared connection**</span></span>  
 <span data-ttu-id="00677-125">보고서 서버에 게시된 공유 데이터 원본을 검색하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00677-125">Select this option to browse to a shared data source that has been published to a report server.</span></span>  
  
 <span data-ttu-id="00677-126">보고서 서버에서 데이터 원본을 선택하면 보고서 작성기와 해당 보고서 서버 간에 연결이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="00677-126">After you select a data source from a report server, Report Builder maintains a connection to this report server.</span></span>  
  
 <span data-ttu-id="00677-127">**내 보고서에 포함된 연결 사용**</span><span class="sxs-lookup"><span data-stu-id="00677-127">**Use a connection embedded in my report**</span></span>  
 <span data-ttu-id="00677-128">이 보고서 전용의 데이터 원본을 만들려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00677-128">Select this option to create a data source that is used only by this report.</span></span>  
  
 <span data-ttu-id="00677-129">**형식**</span><span class="sxs-lookup"><span data-stu-id="00677-129">**Type**</span></span>  
 <span data-ttu-id="00677-130">데이터 처리 확장 프로그램을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00677-130">Select a data processing extension.</span></span> <span data-ttu-id="00677-131">등록된 확장 프로그램이 목록에 모두 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="00677-131">The list displays all registered extensions.</span></span>  
  
 <span data-ttu-id="00677-132">**연결 문자열**</span><span class="sxs-lookup"><span data-stu-id="00677-132">**Connection string**</span></span>  
 <span data-ttu-id="00677-133">데이터 원본에 대한 연결 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="00677-133">Enter a connection string for the data source.</span></span> <span data-ttu-id="00677-134">**연결 속성** 대화 상자를 사용하여 연결 문자열을 작성하려면 **작성** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00677-134">Click **Build** to build the connection string using the **Connection Properties** dialog box.</span></span> <span data-ttu-id="00677-135">식을 편집하려면 **식** (*fx*) 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00677-135">Click the **Expressions** (*fx*) button to edit the expression.</span></span>  
  
 <span data-ttu-id="00677-136">**쿼리 처리 시 단일 트랜잭션 사용**</span><span class="sxs-lookup"><span data-stu-id="00677-136">**Use a single transaction when processing the queries**</span></span>  
 <span data-ttu-id="00677-137">이 데이터 원본을 사용하는 데이터 세트가 데이터베이스에 대해 단일 트랜잭션에서 실행되도록 지정하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="00677-137">Select this option to indicate that datasets that use this data source are run in a single transaction against the database.</span></span> <span data-ttu-id="00677-138">동일한 데이터 원본을 사용하는 하위 보고서에 대한 트랜잭션을 포함하려면 하위 보고서를 선택하고 속성 창에서 **MergeTransactions** 를 **True**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="00677-138">To include transactions for subreports that use the same data source, select the subreport, and in the Properties pane, set **MergeTransactions** to **True**.</span></span>  
  
 <span data-ttu-id="00677-139">**연결 테스트**</span><span class="sxs-lookup"><span data-stu-id="00677-139">**Test Connection**</span></span>  
 <span data-ttu-id="00677-140">데이터 원본 연결이 지정된 자격 증명을 사용하여 작동하는지 확인하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="00677-140">Click to verify that the data source connection works by using the specified credentials.</span></span> <span data-ttu-id="00677-141">연결할 수 없는 경우 자격 증명 및 서버 가용성을 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00677-141">If the connection cannot be made, you need to verify your credentials and the server availability.</span></span> <span data-ttu-id="00677-142">포함된 데이터 원본 및 공유 데이터 원본에 대한 연결을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00677-142">You can test data source connections for embedded and shared data sources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00677-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="00677-143">See Also</span></span>  
 <span data-ttu-id="00677-144">[보고서 &#40;보고서 작성기 및 SSRS&#41;에 데이터를 추가 합니다.](report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="00677-144">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="00677-145">[데이터 연결이 나 데이터 원본 &#40;보고서 작성기 및 SSRS를 추가 하 고 확인&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="00677-145">[Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="00677-146">[보고서 작성기의 데이터 연결, 데이터 원본 및 연결 문자열](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="00677-146">[Data Connections, Data Sources, and Connection Strings in Report Builder](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md) </span></span>  
 <span data-ttu-id="00677-147">[데이터 원본 속성 대화 상자, 자격 증명 &#40;보고서 작성기&#41;](../../2014/reporting-services/data-source-properties-dialog-box-credentials-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="00677-147">[Data Source Properties Dialog Box, Credentials &#40;Report Builder&#41;](../../2014/reporting-services/data-source-properties-dialog-box-credentials-report-builder.md) </span></span>  
 [<span data-ttu-id="00677-148">대화 상자, 창 및 마법사에 대한 보고서 작성기 도움말</span><span class="sxs-lookup"><span data-stu-id="00677-148">Report Builder Help for Dialog Boxes, Panes, and Wizards</span></span>](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)  
  
  

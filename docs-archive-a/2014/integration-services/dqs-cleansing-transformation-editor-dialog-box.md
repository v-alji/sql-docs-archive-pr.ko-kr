---
title: DQS 정리 변환 편집기 대화 상자 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssdqs.designer.cleansing.f1
- SQL12.SSDQS.DESIGNER.DQCONNECTION.F1
ms.assetid: 07e79641-71ee-45d0-a9ba-ed6f9f68f333
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e97cd138bb17ce3cfe476496e5bc576875728224
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646561"
---
# <a name="dqs-cleansing-transformation-editor-dialog-box"></a><span data-ttu-id="65794-102">DQS 정리 변환 편집기 대화 상자</span><span class="sxs-lookup"><span data-stu-id="65794-102">DQS Cleansing Transformation Editor Dialog Box</span></span>
  <span data-ttu-id="65794-103">**DQS 정리 변환 편집기** 대화 상자를 통해 DQS(Data Quality Services)를 사용하여 데이터를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65794-103">Use the **DQS Cleansing Transformation Editor** dialog box to correct data using Data Quality Services (DQS).</span></span> <span data-ttu-id="65794-104">자세한 내용은 [Data Quality Services Concepts](../../2014/data-quality-services/data-quality-services-concepts.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="65794-104">For more information, see [Data Quality Services Concepts](../../2014/data-quality-services/data-quality-services-concepts.md).</span></span>  
  
 <span data-ttu-id="65794-105">변환에 대한 자세한 내용은 [DQS Cleansing Transformation](data-flow/transformations/dqs-cleansing-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="65794-105">To learn more about the transformation, see [DQS Cleansing Transformation](data-flow/transformations/dqs-cleansing-transformation.md).</span></span>  
  
 <span data-ttu-id="65794-106">**수행 작업**</span><span class="sxs-lookup"><span data-stu-id="65794-106">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="65794-107">DQS 정리 변환 편집기 열기</span><span class="sxs-lookup"><span data-stu-id="65794-107">Open the DQS Cleansing Transformation Editor</span></span>](#open)  
  
-   [<span data-ttu-id="65794-108">연결 관리자 탭에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="65794-108">Set options on the Connection Manager tab</span></span>](#connection)  
  
-   [<span data-ttu-id="65794-109">매핑 탭에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="65794-109">Set options on the Mapping tab</span></span>](#mapping)  
  
-   [<span data-ttu-id="65794-110">고급 탭에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="65794-110">Set options on the Advanced tab</span></span>](#advanced)  
  
-   [<span data-ttu-id="65794-111">DQS 정리 연결 관리자 대화 상자에서 옵션을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="65794-111">Set the options in the DQS Cleansing Connection Manager dialog box</span></span>](#manager)  
  
##  <a name="open-the-dqs-cleansing-transformation-editor"></a><a name="open"></a><span data-ttu-id="65794-112">DQS 정리 변환 편집기 열기</span><span class="sxs-lookup"><span data-stu-id="65794-112">Open the DQS Cleansing Transformation Editor</span></span>  
  
1.  <span data-ttu-id="65794-113">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]패키지에 DQS 정리 변환을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="65794-113">Add the DQS Cleansing Transformation to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="65794-114">구성 요소를 마우스 오른쪽 단추로 클릭한 다음 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65794-114">Right-click the component and then click **Edit**.</span></span>  
  
##  <a name="set-options-on-the-connection-manager-tab"></a><a name="connection"></a> <span data-ttu-id="65794-115">연결 관리자 탭에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="65794-115">Set options on the Connection Manager tab</span></span>  
 <span data-ttu-id="65794-116">**데이터 품질 연결 관리자**</span><span class="sxs-lookup"><span data-stu-id="65794-116">**Data quality connection manager**</span></span>  
 <span data-ttu-id="65794-117">목록에서 기존 DQS 연결 관리자를 선택하거나 **새로 만들기**를 클릭하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="65794-117">Select an existing DQS connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="65794-118">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="65794-118">**New**</span></span>  
 <span data-ttu-id="65794-119">**DQS 정리 연결 관리자** 대화 상자를 사용하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="65794-119">Create a new connection manager by using the **DQS Cleansing Connection Manager** dialog box.</span></span> <span data-ttu-id="65794-120">[DQS 정리 연결 관리자 대화 상자에서 옵션 설정](#manager)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="65794-120">See [Set the options in the DQS Cleansing Connection Manager dialog box](#manager)</span></span>  
  
 <span data-ttu-id="65794-121">**데이터 품질 기술 자료**</span><span class="sxs-lookup"><span data-stu-id="65794-121">**Data Quality Knowledge Base**</span></span>  
 <span data-ttu-id="65794-122">연결된 데이터 원본에 대한 기존 DQS 기술 자료를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="65794-122">Select an existing DQS knowledge base for the connected data source.</span></span> <span data-ttu-id="65794-123">DQS 기술 자료에 대한 자세한 내용은 [DQS Knowledge Bases and Domains](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="65794-123">For more information about the DQS knowledge base, see [DQS Knowledge Bases and Domains](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md).</span></span>  
  
 <span data-ttu-id="65794-124">**연결 암호화**</span><span class="sxs-lookup"><span data-stu-id="65794-124">**Encrypt connection**</span></span>  
 <span data-ttu-id="65794-125">DQS 서버와 간 데이터 전송을 암호화 하기 위해 연결을 암호화할지 여부를 지정 합니다 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="65794-125">specify whether to encrypt the connection, in order to encrypt the data transfer between the DQS Server and [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="65794-126">**사용 가능한 도메인**</span><span class="sxs-lookup"><span data-stu-id="65794-126">**Available domains**</span></span>  
 <span data-ttu-id="65794-127">선택한 기술 자료에 사용 가능한 도메인을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="65794-127">Lists the available domains for the selected knowledge base.</span></span> <span data-ttu-id="65794-128">단일 도메인과 둘 이상의 단일 도메인을 포함하는 복합 도메인의 두 가지 도메인 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65794-128">There are two types of domains: single domains, and composite domains that contain two or more single domains.</span></span>  
  
 <span data-ttu-id="65794-129">복합 도메인에 열을 매핑하는 방법은 [Map Columns to Composite Domains](data-flow/transformations/map-columns-to-composite-domains.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="65794-129">For information on how to map columns to composite domains, see [Map Columns to Composite Domains](data-flow/transformations/map-columns-to-composite-domains.md).</span></span>  
  
 <span data-ttu-id="65794-130">도메인에 대한 자세한 내용은 [DQS Knowledge Bases and Domains](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="65794-130">For more information about domains, see [DQS Knowledge Bases and Domains](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md).</span></span>  
  
 <span data-ttu-id="65794-131">**오류 출력 구성**</span><span class="sxs-lookup"><span data-stu-id="65794-131">**Configure Error Output**</span></span>  
 <span data-ttu-id="65794-132">행 수준 오류 처리 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="65794-132">Specify how to handle row-level errors.</span></span> <span data-ttu-id="65794-133">변환에서 연결된 데이터 원본의 데이터를 수정할 때 예기치 않은 데이터 값 또는 유효성 검사 제약 조건으로 인해 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65794-133">Errors can occur when the transformation corrects data from the connected data source, due to unexpected data values or validation constraints.</span></span>  
  
 <span data-ttu-id="65794-134">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="65794-134">The following are the valid values:</span></span>  
  
-   <span data-ttu-id="65794-135">**구성 요소 실패**- 변환에 실패하여 Data Quality Services 데이터베이스에 입력 데이터가 삽입되지 않았음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65794-135">**Fail Component**, which indicates that the transformation fails and the input data is not inserted into the Data Quality Services database.</span></span> <span data-ttu-id="65794-136">기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="65794-136">This is the default value.</span></span>  
  
-   <span data-ttu-id="65794-137">**행 리디렉션**- 입력 데이터가 Data Quality Services 데이터베이스에 삽입되지 않고 오류 출력으로 리디렉션되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65794-137">**Redirect Row**, which indicates that the input data is not inserted into the Data Quality Services database and is redirected to the error output.</span></span>  
  
##  <a name="set-options-on-the-mapping-tab"></a><a name="mapping"></a><span data-ttu-id="65794-138">매핑 탭에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="65794-138">Set options on the Mapping tab</span></span>  
 <span data-ttu-id="65794-139">복합 도메인에 열을 매핑하는 방법은 [Map Columns to Composite Domains](data-flow/transformations/map-columns-to-composite-domains.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="65794-139">For information on how to map columns to composite domains, see [Map Columns to Composite Domains](data-flow/transformations/map-columns-to-composite-domains.md).</span></span>  
  
 <span data-ttu-id="65794-140">**사용 가능한 입력 열**</span><span class="sxs-lookup"><span data-stu-id="65794-140">**Available Input Columns**</span></span>  
 <span data-ttu-id="65794-141">연결된 데이터 원본의 열을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="65794-141">Lists the columns from the connected data source.</span></span> <span data-ttu-id="65794-142">수정할 데이터가 들어 있는 하나 이상의 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="65794-142">Select one or more columns that contain data that you want to correct.</span></span>  
  
 <span data-ttu-id="65794-143">**입력 열**</span><span class="sxs-lookup"><span data-stu-id="65794-143">**Input Column**</span></span>  
 <span data-ttu-id="65794-144">**사용 가능한 입력 열** 영역에서 선택한 입력 열을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="65794-144">Lists an input column that you selected in the **Available Input Columns** area.</span></span>  
  
 <span data-ttu-id="65794-145">**도메인**</span><span class="sxs-lookup"><span data-stu-id="65794-145">**Domain**</span></span>  
 <span data-ttu-id="65794-146">입력 열에 매핑할 도메인을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="65794-146">Select a domain to map to the input column.</span></span>  
  
 <span data-ttu-id="65794-147">**원본 별칭**</span><span class="sxs-lookup"><span data-stu-id="65794-147">**Source Alias**</span></span>  
 <span data-ttu-id="65794-148">원래 열 값이 들어 있는 원본 열을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="65794-148">Lists the source column that contains the original column value.</span></span>  
  
 <span data-ttu-id="65794-149">열 이름을 수정할 필드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65794-149">Click in the field to modify the column name.</span></span>  
  
 <span data-ttu-id="65794-150">**출력 별칭**</span><span class="sxs-lookup"><span data-stu-id="65794-150">**Output Alias**</span></span>  
 <span data-ttu-id="65794-151">**DQS 정리 변환**을 통해 출력될 열을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="65794-151">Lists the column that is outputted by the **DQS Cleansing Transformation**.</span></span> <span data-ttu-id="65794-152">원래 열 값 또는 수정된 값이 들어 있는 열입니다.</span><span class="sxs-lookup"><span data-stu-id="65794-152">The column contains the original column value or the corrected value.</span></span>  
  
 <span data-ttu-id="65794-153">열 이름을 수정할 필드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65794-153">Click in the field to modify the column name.</span></span>  
  
 <span data-ttu-id="65794-154">**상태 별칭**</span><span class="sxs-lookup"><span data-stu-id="65794-154">**Status Alias**</span></span>  
 <span data-ttu-id="65794-155">수정된 데이터에 대한 상태 정보가 들어 있는 열을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="65794-155">Lists the column that contains status information for the corrected data.</span></span> <span data-ttu-id="65794-156">열 이름을 수정할 필드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65794-156">Click in the field to modify the column name.</span></span>  
  
##  <a name="set-options-on-the-advanced-tab"></a><a name="advanced"></a><span data-ttu-id="65794-157">고급 탭에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="65794-157">Set options on the Advanced tab</span></span>  
 <span data-ttu-id="65794-158">**출력 표준화**</span><span class="sxs-lookup"><span data-stu-id="65794-158">**Standardize output**</span></span>  
 <span data-ttu-id="65794-159">도메인에 대해 정의된 출력 형식을 기반으로 표준화된 형식으로 데이터를 출력할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65794-159">Indicate whether to output the data in the standardized format based on the output format defined for domains.</span></span> <span data-ttu-id="65794-160">표준화된 형식에 대한 자세한 내용은 [데이터 정리](../../2014/data-quality-services/data-cleansing.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="65794-160">For more information about standardized format, see [Data Cleansing](../../2014/data-quality-services/data-cleansing.md).</span></span>  
  
 <span data-ttu-id="65794-161">**신뢰도**</span><span class="sxs-lookup"><span data-stu-id="65794-161">**Confidence**</span></span>  
 <span data-ttu-id="65794-162">수정된 데이터에 대한 신뢰 수준을 포함할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65794-162">Indicate whether to include the confidence level for corrected data.</span></span> <span data-ttu-id="65794-163">신뢰 수준은 수정 내용 또는 제안 내용에 대한 DQS의 확신도를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65794-163">The confidence level indicates the extend of certainty of DQS for the correction or suggestion.</span></span> <span data-ttu-id="65794-164">신뢰 수준에 대한 자세한 내용은 [데이터 정리](../../2014/data-quality-services/data-cleansing.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="65794-164">For more information about confidence levels, see [Data Cleansing](../../2014/data-quality-services/data-cleansing.md).</span></span>  
  
 <span data-ttu-id="65794-165">**이유**</span><span class="sxs-lookup"><span data-stu-id="65794-165">**Reason**</span></span>  
 <span data-ttu-id="65794-166">데이터 수정 이유를 포함할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65794-166">Indicate whether to include the reason for the data correction.</span></span>  
  
 <span data-ttu-id="65794-167">**추가된 데이터**</span><span class="sxs-lookup"><span data-stu-id="65794-167">**Appended Data**</span></span>  
 <span data-ttu-id="65794-168">기존 참조 데이터 공급자에서 받은 추가 데이터를 출력할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65794-168">Indicate whether to output additional data that is received from an existing reference data provider.</span></span> <span data-ttu-id="65794-169">자세한 내용은 [Reference Data Services in DQS](../../2014/data-quality-services/reference-data-services-in-dqs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="65794-169">For more information, see [Reference Data Services in DQS](../../2014/data-quality-services/reference-data-services-in-dqs.md).</span></span>  
  
 <span data-ttu-id="65794-170">**추가된 데이터 스키마**</span><span class="sxs-lookup"><span data-stu-id="65794-170">**Appended Data Schema**</span></span>  
 <span data-ttu-id="65794-171">데이터 스키마를 출력할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65794-171">Indicate whether to output the data schema.</span></span> <span data-ttu-id="65794-172">자세한 내용은 [참조 데이터에 도메인 또는 복합 도메인 연결](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="65794-172">For more information, see [Attach a Domain or Composite Domain to Reference Data](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md).</span></span>  
  
##  <a name="set-the-options-in-the-dqs-cleansing-connection-manager-dialog-box"></a><a name="manager"></a><span data-ttu-id="65794-173">DQS 정리 연결 관리자 대화 상자에서 옵션을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="65794-173">Set the options in the DQS Cleansing Connection Manager dialog box</span></span>  
 <span data-ttu-id="65794-174">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="65794-174">**Server name**</span></span>  
 <span data-ttu-id="65794-175">연결할 DQS 서버의 이름을 선택하거나 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="65794-175">Select or type the name of the DQS server that you want to connect to.</span></span> <span data-ttu-id="65794-176">서버에 대한 자세한 내용은 [DQS Administration](../../2014/data-quality-services/dqs-administration.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="65794-176">For more information about the server, see [DQS Administration](../../2014/data-quality-services/dqs-administration.md).</span></span>  
  
 <span data-ttu-id="65794-177">**연결 테스트**</span><span class="sxs-lookup"><span data-stu-id="65794-177">**Test Connection**</span></span>  
 <span data-ttu-id="65794-178">지정한 연결이 표시되는지 확인하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65794-178">Click to confirm that the connection that you specified is viable.</span></span>  
  
 <span data-ttu-id="65794-179">다음을 수행하여 연결 영역에서 **DQS 정리 연결 관리자** 대화 상자를 열 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65794-179">You can also open the **DQS Cleansing Connection Manager** dialog box from the connections area, by doing the following:</span></span>  
  
1.  <span data-ttu-id="65794-180">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 기존 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 열거나 새 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="65794-180">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open an existing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project or create a new one.</span></span>  
  
2.  <span data-ttu-id="65794-181">연결 영역을 마우스 오른쪽 단추로 클릭하고 **새 연결**을 클릭한 다음 **DQS**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65794-181">Right-click in the connections area, click **New Connection**, and then click **DQS**.</span></span>  
  
3.  <span data-ttu-id="65794-182">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65794-182">Click **Add**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65794-183">참고 항목</span><span class="sxs-lookup"><span data-stu-id="65794-183">See Also</span></span>  
 [<span data-ttu-id="65794-184">데이터 원본에 데이터 품질 규칙 적용</span><span class="sxs-lookup"><span data-stu-id="65794-184">Apply Data Quality Rules to Data Source</span></span>](data-flow/transformations/apply-data-quality-rules-to-data-source.md)  
  
  

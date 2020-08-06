---
title: 도메인으로 정리 프로젝트 값 가져오기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.kb.importprojectvalues.f1
ms.assetid: f23e38e2-39e0-42d7-abd5-34d8fcca5d2a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 38616da5a0a8fb9c8f149d9f55a08b63dee5ff6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732043"
---
# <a name="import-cleansing-project-values-into-a-domain"></a><span data-ttu-id="5445b-102">도메인으로 정리 프로젝트 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="5445b-102">Import Cleansing Project Values into a Domain</span></span>
  <span data-ttu-id="5445b-103">DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] )에서는 데이터 품질 정리 프로젝트나 DQS 정리 구성 요소가 포함된 Integration Services 패키지에서 정리 프로세스 중에 수집된 데이터 품질 기술 자료를 도메인으로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-103">In [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS), you can import data quality knowledge gathered during the cleansing process in a data quality cleansing project or an Integration Services package containing the DQS Cleansing component into a domain.</span></span> <span data-ttu-id="5445b-104">이렇게 하면 신뢰할 수 있는 정보가 손실되지 않고 기술 자료가 지속적으로 개선됩니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-104">This ensures that trusted knowledge is not lost, and that the knowledge base is continually improved.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5445b-105">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="5445b-105">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="5445b-106">필수 조건</span><span class="sxs-lookup"><span data-stu-id="5445b-106">Prerequisites</span></span>  
  
-   <span data-ttu-id="5445b-107">Data Quality 클라이언트의 정리 프로젝트나 DQS 정리 구성 요소가 포함된 Integration Services 패키지에서 도메인을 사용한 경우에만 정리 프로젝트 값을 도메인으로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-107">To import cleansing project values into a domain, the domain must have been used in the cleansing project in Data Quality Client or in the Integration Services package containing a DQS Cleansing component.</span></span>  
  
-   <span data-ttu-id="5445b-108">Data Quality 클라이언트의 정리 프로젝트나 DQS 정리 구성 요소가 포함된 Integration Services 패키지가 올바르게 완료된 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-108">The cleansing project in Data Quality Client or the Integration Services package containing the DQS Cleansing component must have successfully completed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5445b-109">보안</span><span class="sxs-lookup"><span data-stu-id="5445b-109">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5445b-110">권한</span><span class="sxs-lookup"><span data-stu-id="5445b-110">Permissions</span></span>  
 <span data-ttu-id="5445b-111">정리 프로세스 도중 수집된 데이터 품질 기술 자료를 도메인으로 가져오려면 DQS_MAIN 데이터베이스에 대한 dqs_kb_editor 또는 dqs_administrator 역할이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-111">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to import data quality knowledge gathered during the cleansing process into a domain.</span></span>  
  
##  <a name="import-cleansing-project-values"></a><a name="Import"></a> <span data-ttu-id="5445b-112">정리 프로젝트 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="5445b-112">Import Cleansing Project Values</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="5445b-113">[Data Quality Client 응용 프로그램을 실행](../../2014/data-quality-services/run-the-data-quality-client-application.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-113">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="5445b-114">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면의 도메인 관리 작업에서 기술 자료를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-114">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open a knowledge base in the Domain Management activity.</span></span>  
  
3.  <span data-ttu-id="5445b-115">기존 도메인에 값을 추가하는 경우 도메인 목록에서 도메인을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-115">If adding values to an existing domain, select the domain in the domain list.</span></span>  
  
4.  <span data-ttu-id="5445b-116">**도메인 값** 탭을 클릭하고 아이콘 표시줄에서 **값 가져오기** 아이콘을 클릭한 후 **프로젝트 값 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-116">Click the **Domain Values** tab, click the **Import Values** icon in the icon bar, and then click **Import project values**.</span></span> <span data-ttu-id="5445b-117">**프로젝트 값 가져오기** 대화 상자가 나타나고 도메인을 사용하여 정리한 데이터 품질 프로젝트 및 Integration Services 패키지의 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-117">The **Import Project Values** dialog box appears with a list of data quality projects and Integration Services packages that were cleansed using the domain.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5445b-118">해당 도메인이나 연결된 도메인을 사용하여 프로젝트가 생성되지 않았거나 프로젝트가 완료되지 않은 경우 **프로젝트 값 가져오기** 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-118">If no project has been created using the domain or any of its linked domains, or the project was not finished, the **Import project values** option will not be available.</span></span>  
  
5.  <span data-ttu-id="5445b-119">**프로젝트 값 가져오기** 대화 상자에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-119">In the **Import Project Values** dialog box:</span></span>  
  
    -   <span data-ttu-id="5445b-120">**가져옴** 드롭다운 목록에서 모든 프로젝트를 표시하려면 **모두** 를 선택하고, 값을 아직 가져오지 않은 프로젝트만 표시하려면 **아니요** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-120">Select **All** in the **Imported** drop-down list to display all projects, or **No** to display only projects whose values have not been imported yet.</span></span>  
  
    -   <span data-ttu-id="5445b-121">가져올 값이 있는 프로젝트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-121">Select the project that you want to import values from.</span></span>  
  
    -   <span data-ttu-id="5445b-122">**새 탭에서 값 추가** 를 선택하여 **올바름** 및 **수정됨** 탭의 값 외에 새 탭의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-122">Select **Add values from New tab** to import values in the new tab, in addition to values in the **Correct** and **Corrected** tabs.</span></span>  
  
    -   <span data-ttu-id="5445b-123">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-123">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="5445b-124">**도메인 값** 탭으로 전환되고 값을 가져왔다는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-124">You return to the **Domain Values** tab, and a message is displayed on successful import of the values.</span></span> <span data-ttu-id="5445b-125">가져와서 도메인에 새로 추가된 값이 **값** 테이블에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-125">Values that have been imported, and so are new to the domain, will be displayed in the **Values** table.</span></span>  
  
7.  <span data-ttu-id="5445b-126">**새 항목만 표시** 를 선택 취소하여 도메인에 있는 모든 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-126">Deselect **Show Only New** to display all values that are in the domain.</span></span>  
  
8.  <span data-ttu-id="5445b-127">**올바름**, **오류**또는 **유효하지 않음** 을 선택하여 선택한 형식의 해당 값만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-127">Select **Correct**, **Error**, or **Invalid** to display only those values of the selected type.</span></span>  
  
9. <span data-ttu-id="5445b-128">특정 문자열을 검색하려면 **찾기** 입력란에 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-128">To search for a specific string, enter the string in the **Find** text box.</span></span> <span data-ttu-id="5445b-129">위쪽 또는 아래쪽 화살표를 클릭하여 검색 조건에 맞는 값 사이를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-129">Click the up or down arrow to step through the values that meet the search criteria.</span></span> <span data-ttu-id="5445b-130">이러한 값은 노란색으로 강조 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-130">They will be highlighted in yellow.</span></span>  
  
10. <span data-ttu-id="5445b-131">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-131">Click **Finish**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5445b-132">**도메인 값** 탭의 값에 대한 작업 방법은 [Change Domain Values](../../2014/data-quality-services/change-domain-values.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5445b-132">For more information on working with values in the **Domain Values** tab, see [Change Domain Values](../../2014/data-quality-services/change-domain-values.md).</span></span>  
  
##  <a name="follow-up-after-importing-project-values-into-a-domain"></a><a name="FollowUp"></a><span data-ttu-id="5445b-133">후속 작업: 도메인에 프로젝트 값을 가져온 후</span><span class="sxs-lookup"><span data-stu-id="5445b-133">Follow Up: After Importing Project Values into a Domain</span></span>  
 <span data-ttu-id="5445b-134">정리 프로세스 도중 수집된 데이터 품질 기술 자료를 도메인으로 가져온 후 도메인 및 값에 대해 다른 도메인 관리 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-134">After you import data quality knowledge gathered during the cleansing process into a domain, you can perform other domain management tasks on the domain and the values.</span></span> <span data-ttu-id="5445b-135">자세한 내용은 [도메인 관리](../../2014/data-quality-services/managing-a-domain.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5445b-135">For more information, see [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md).</span></span>  
  
##  <a name="values-that-will-be-imported"></a><a name="Values"></a><span data-ttu-id="5445b-136">가져올 값</span><span class="sxs-lookup"><span data-stu-id="5445b-136">Values that Will Be Imported</span></span>  
 <span data-ttu-id="5445b-137">프로젝트에서 도메인으로 가져올 수 있는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-137">The following values will be imported from a project into a domain:</span></span>  
  
-   <span data-ttu-id="5445b-138">문자열 값만 도메인으로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-138">Only string values are imported to the domain.</span></span>  
  
-   <span data-ttu-id="5445b-139">**정리**작업의 **결과 관리 및 보기**페이지에 있는 **수정** , **수정됨** 및 **새로 만들기** 탭의 값만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-139">Only values from the **Correct**, **Corrected**, and **New** tabs on the **Manage and View results** page of the **Cleansing** activity will be imported.</span></span> <span data-ttu-id="5445b-140">**프로젝트 값 가져오기** 대화 상자에서 **새 탭에서 값 추가** 확인란을 선택한 경우에만 **새로 만들기** 탭에 있는 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-140">Values from the **New** tab will be imported only if the **Add values from New tab** check box in the **Import Project Values** dialog box has been selected.</span></span>  
  
-   <span data-ttu-id="5445b-141">값은 올바른 값 또는 수정 사항이 있는 오류로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-141">Values will be imported as correct or as an error with its correction.</span></span> <span data-ttu-id="5445b-142">수정 값이 있는 오류 값만 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-142">Only an error value with a correction value will be imported.</span></span>  
  
-   <span data-ttu-id="5445b-143">수정 값은 기술 자료에 없는 새 값이거나 기존의 올바른 값입니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-143">The correction value will be either a new value that does not exist in the knowledge base or an existing correct value.</span></span>  
  
-   <span data-ttu-id="5445b-144">레코드 수준이 아닌 값 수준에서 수행된 수정 사항만 기술 자료로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-144">Only corrections performed on the value level, not the record level, will be imported into the knowledge base.</span></span>  
  
-   <span data-ttu-id="5445b-145">가져온 값이 도메인 규칙과 충돌하면 유효하지 않은 값이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-145">Invalid values will be created if the imported value contradicts a domain rule.</span></span>  
  
-   <span data-ttu-id="5445b-146">한 번에 여러 프로젝트에서 값을 가져오면 값이 순서대로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-146">If you import values from several projects at once, the values are imported in a sequential order.</span></span>  
  
-   <span data-ttu-id="5445b-147">도메인의 용어 기반 관계의 결과로 만들어진 수정 사항은 올바른 값(오류 아님)으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-147">A correction made as a result of a term-based relation in a domain is imported as a correct value (not as an error).</span></span>  
  
##  <a name="values-that-will-not-be-imported"></a><a name="ValuesNot"></a><span data-ttu-id="5445b-148">가져올 수 없는 값</span><span class="sxs-lookup"><span data-stu-id="5445b-148">Values that Will Not Be Imported</span></span>  
 <span data-ttu-id="5445b-149">프로젝트에서 도메인으로 가져올 수 없는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-149">The following values will not be imported from a project into a domain:</span></span>  
  
-   <span data-ttu-id="5445b-150">**정리** 작업의 **결과 관리 및 보기** 페이지에서 **제안** 및 **유효하지 않음** 탭의 값은 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-150">Values from the **Suggested** and **Invalid** tabs on the **Manage and View results** page of the **Cleansing** activity will not be imported.</span></span>  
  
-   <span data-ttu-id="5445b-151">정리 프로젝트에 있는 값이 도메인의 기존 값과 충돌할 경우 프로젝트에 있는 값이 생략됩니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-151">If a value found in the cleansing project contradicts an existing value in the domain, the value found in the project is skipped.</span></span> <span data-ttu-id="5445b-152">정리 및 기술 자료 값 사이의 충돌도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-152">This will include conflicts between cleansing and knowledge base values.</span></span>  
  
-   <span data-ttu-id="5445b-153">레코드 수준에서 수행된 수정 사항은 기술 자료로 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-153">Corrections performed on the record level will not be imported into the knowledge base.</span></span>  
  
-   <span data-ttu-id="5445b-154">대체 값이 참조 데이터 서비스에 의해 수정되거나 올바른 것으로 승인된 경우 도메인으로 값을 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-154">No value will be imported to a domain if the value that it would replace was corrected or approved as correct by a reference data service.</span></span>  
  
-   <span data-ttu-id="5445b-155">수정 값이 기술 자료에서 유효하지 않은 값 또는 오류 값으로 표시될 경우 오류 또는 수정 값을 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-155">If a correction value appears in the knowledge base as an invalid or error value, neither the error nor the correction value will be imported.</span></span>  
  
-   <span data-ttu-id="5445b-156">도메인이 복합 도메인의 일부이고 정리가 복합 도메인에 대해 수행된 경우 값을 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-156">If the domain is part of a composite domain, and the cleansing was performed on the composite domain, no values will be imported.</span></span>  
  
-   <span data-ttu-id="5445b-157">기술 자료가 작업 중인 상태이고 가져오기 작업을 수행하는 사용자에 의해 잠긴 경우에만 프로젝트에서 값을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5445b-157">You can import values from a project only when the knowledge base has a state of in-work and the knowledge base is locked by the user who is importing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5445b-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5445b-158">See Also</span></span>  
 <span data-ttu-id="5445b-159">[데이터 정리](../../2014/data-quality-services/data-cleansing.md) </span><span class="sxs-lookup"><span data-stu-id="5445b-159">[Data Cleansing](../../2014/data-quality-services/data-cleansing.md) </span></span>  
 [<span data-ttu-id="5445b-160">DQS 정리 변환</span><span class="sxs-lookup"><span data-stu-id="5445b-160">DQS Cleansing Transformation</span></span>](../integration-services/data-flow/transformations/dqs-cleansing-transformation.md)  
  
  

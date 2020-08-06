---
title: 일반 속성 페이지, 공유 데이터 집합 (보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 10798e41-24c3-4e69-893b-7ee6af7fc958
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 31825e61cb40505e9167cc2b930a5b79e5aaa013
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661530"
---
# <a name="general-properties-page-shared-datasets-report-manager"></a><span data-ttu-id="d3f4f-102">일반 속성 페이지, 공유 데이터 세트(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="d3f4f-102">General Properties Page, Shared Datasets (Report Manager)</span></span>
  <span data-ttu-id="d3f4f-103">공유 데이터 세트 페이지를 사용하여 공유 데이터 세트 항목의 속성을 보고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-103">Use the Shared Dataset page to view and manage properties for a shared dataset item.</span></span>  
  
 <span data-ttu-id="d3f4f-104">보고서 관리자에서는 쿼리를 비롯한 공유 데이터 세트 정의를 보거나 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-104">From Report Manager, you cannot view or change the shared dataset definition, including the query.</span></span> <span data-ttu-id="d3f4f-105">정의를 변경하려면 제작 도구를 사용하여 정의를 열고 수정한 다음 보고서 서버에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-105">To change the definition, you must use an authoring tool to open and modify the definition and then save it to the report server.</span></span>  
  
 <span data-ttu-id="d3f4f-106">공유 데이터 세트를 사용하면 데이터 세트의 설정을, 해당 설정을 사용하는 보고서, 구성 요소 및 기타 카탈로그 항목과 별도로 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-106">With a shared dataset, you can manage the settings for a dataset separately from reports, components, and other catalog items that use it.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="d3f4f-107">탐색</span><span class="sxs-lookup"><span data-stu-id="d3f4f-107">Navigation</span></span>  
 <span data-ttu-id="d3f4f-108">사용자 인터페이스(UI)에서 이 위치를 탐색하려면 다음 절차를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-108">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-shared-dataset-properties-page-for-a-shared-dataset"></a><span data-ttu-id="d3f4f-109">공유 데이터 세트의 공유 데이터 세트 속성 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="d3f4f-109">To open the Shared Dataset properties page for a shared dataset</span></span>  
  
1.  <span data-ttu-id="d3f4f-110">보고서 관리자를 열고 속성을 구성할 공유 데이터 세트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-110">Open Report Manager, and locate shared dataset for which you want to configure properties.</span></span>  
  
2.  <span data-ttu-id="d3f4f-111">공유 데이터 세트 위로 마우스를 이동하고 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-111">Hover over the shared dataset, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="d3f4f-112">드롭다운 목록에서 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-112">In the drop-down list, click **Manage**.</span></span> <span data-ttu-id="d3f4f-113">일반 속성 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-113">The General properties page opens.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d3f4f-114">옵션</span><span class="sxs-lookup"><span data-stu-id="d3f4f-114">Options</span></span>  
 <span data-ttu-id="d3f4f-115">**이름**</span><span class="sxs-lookup"><span data-stu-id="d3f4f-115">**Name**</span></span>  
 <span data-ttu-id="d3f4f-116">보고서 서버 폴더 계층 구조에서 항목을 식별하는 데 사용되는 공유 데이터 세트의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-116">Type a name for the shared dataset that is used to identify the item within the report server folder hierarchy.</span></span>  
  
 <span data-ttu-id="d3f4f-117">**설명**</span><span class="sxs-lookup"><span data-stu-id="d3f4f-117">**Description**</span></span>  
 <span data-ttu-id="d3f4f-118">공유 데이터 세트에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-118">Provide information about the shared dataset.</span></span> <span data-ttu-id="d3f4f-119">이 설명은 내용 페이지에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-119">This description appears on the Contents page.</span></span>  
  
 <span data-ttu-id="d3f4f-120">**목록 뷰에서 숨기기**</span><span class="sxs-lookup"><span data-stu-id="d3f4f-120">**Hide in list view**</span></span>  
 <span data-ttu-id="d3f4f-121">보고서 관리자에서 목록 뷰 모드를 사용하는 사용자가 볼 수 없게 공유 데이터 세트를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-121">Hide the shared dataset from users who are using list view mode in Report Manager.</span></span> <span data-ttu-id="d3f4f-122">목록 뷰 모드는 보고서 서버 폴더 계층을 검색할 때 표시되는 기본 뷰 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-122">List view mode is the default view format when browsing the report server folder hierarchy.</span></span> <span data-ttu-id="d3f4f-123">목록 뷰에서 항목 이름과 설명은 페이지에 가로로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-123">In list view, item names and descriptions flow across the page.</span></span> <span data-ttu-id="d3f4f-124">이 외에도 자세히 보기를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-124">The alternative format is details view.</span></span> <span data-ttu-id="d3f4f-125">자세히 보기는 설명을 표시하지 않지만 항목에 대한 다른 정보는 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-125">Details view omits descriptions, but includes other information about the item.</span></span> <span data-ttu-id="d3f4f-126">목록 뷰에서는 항목을 숨길 수 있지만 자세히 보기에서는 항목을 숨길 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-126">Although you can hide an item in list view, you cannot hide an item in details view.</span></span> <span data-ttu-id="d3f4f-127">항목에 대한 액세스를 제한하려면 역할 할당을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-127">If you want to restrict access to an item, you must create a role assignment.</span></span>  
  
 <span data-ttu-id="d3f4f-128">**쿼리 실행 제한 시간**</span><span class="sxs-lookup"><span data-stu-id="d3f4f-128">**Query execution timeout**</span></span>  
 <span data-ttu-id="d3f4f-129">쿼리 시간이 초과 될 때 까지의 시간 (초)을 입력 합니다. 0 인 경우 쿼리 시간이 제한 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-129">Type the number of seconds until the query times out. If it is 0, the query does not time out.</span></span>  
  
 <span data-ttu-id="d3f4f-130">**적용**</span><span class="sxs-lookup"><span data-stu-id="d3f4f-130">**Apply**</span></span>  
 <span data-ttu-id="d3f4f-131">변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-131">Save your changes.</span></span>  
  
 <span data-ttu-id="d3f4f-132">**삭제**</span><span class="sxs-lookup"><span data-stu-id="d3f4f-132">**Delete**</span></span>  
 <span data-ttu-id="d3f4f-133">보고서 서버 데이터베이스에서 공유 데이터 세트를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-133">Remove the shared dataset from the report server database.</span></span> <span data-ttu-id="d3f4f-134">공유 데이터 세트를 삭제하면 보고서 또는 캐시된 버전이 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-134">Deleting a shared dataset deactivates any reports or cached versions.</span></span> <span data-ttu-id="d3f4f-135">보고서를 다시 활성화하려면 보고서 제작 도구에서 해당 보고서를 열고 동일한 이름과 동일한 필드 컬렉션을 갖는 데이터 세트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-135">To reactivate a report, you must open each one in a report authoring tool, and specify a dataset with the same name and the same field collection.</span></span> <span data-ttu-id="d3f4f-136">또는 동일한 필드 컬렉션을 갖는 다른 데이터 세트를 사용하도록 각 데이터 영역 참조를 업데이트할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-136">Alternatively, you can update each data region reference to use a different dataset with the same field collection.</span></span>  
  
 <span data-ttu-id="d3f4f-137">**이동**</span><span class="sxs-lookup"><span data-stu-id="d3f4f-137">**Move**</span></span>  
 <span data-ttu-id="d3f4f-138">보고서 서버 폴더 계층 구조 내의 다른 위치로 공유 데이터 세트를 옮깁니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-138">Relocate a shared dataset within the report server folder hierarchy.</span></span> <span data-ttu-id="d3f4f-139">이 단추를 클릭하면 폴더를 검색하여 새 폴더 위치를 찾을 수 있는 항목 이동 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-139">Clicking this button opens the Move Items page, on which you can browse through folders for a new folder location.</span></span> <span data-ttu-id="d3f4f-140">자세한 내용은 [항목 이동 페이지 &#40;보고서 관리자&#41;](../../2014/reporting-services/move-items-page-report-manager.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-140">For more information, see [Move Items Page &#40;Report Manager&#41;](../../2014/reporting-services/move-items-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="d3f4f-141">**다운로드**</span><span class="sxs-lookup"><span data-stu-id="d3f4f-141">**Download**</span></span>  
 <span data-ttu-id="d3f4f-142">공유 데이터 세트 정의의 복사본을 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-142">Extract a copy of the shared dataset definition.</span></span> <span data-ttu-id="d3f4f-143">컴퓨터에 정의된 파일 연결에 따라 파일이 Visual Studio 또는 다른 애플리케이션에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-143">Depending on the file associations defined on your computer, the file will open in Visual Studio or a different application.</span></span> <span data-ttu-id="d3f4f-144">대부분의 경우 공유 데이터 세트는 XML 파일로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-144">In most cases, the shared dataset opens as an XML file.</span></span>  
  
 <span data-ttu-id="d3f4f-145">**바꾸기**</span><span class="sxs-lookup"><span data-stu-id="d3f4f-145">**Replace**</span></span>  
 <span data-ttu-id="d3f4f-146">파일 시스템에 있는 .rsd 파일의 다른 정의로 공유 데이터 세트 정의를 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="d3f4f-146">Replace the shared dataset definition with a different one from an .rsd file located on the file system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3f4f-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d3f4f-147">See Also</span></span>  
 <span data-ttu-id="d3f4f-148">[보고서 관리자&#40;SSRS 기본 모드&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="d3f4f-148">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="d3f4f-149">[내용 페이지 &#40;보고서 관리자&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="d3f4f-149">[Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="d3f4f-150">[F1 도움말 보고서 관리자](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="d3f4f-150">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="d3f4f-151">[캐시 새로 고침 옵션을 보고서 관리자 &#40;&#41;](../../2014/reporting-services/cache-refresh-options-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="d3f4f-151">[Cache Refresh Options &#40;Report Manager&#41;](../../2014/reporting-services/cache-refresh-options-report-manager.md) </span></span>  
 <span data-ttu-id="d3f4f-152">[캐싱 페이지, 공유 데이터 집합 &#40;보고서 관리자&#41;](../../2014/reporting-services/caching-page-shared-datasets-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="d3f4f-152">[Caching Page, Shared Datasets &#40;Report Manager&#41;](../../2014/reporting-services/caching-page-shared-datasets-report-manager.md) </span></span>  
 <span data-ttu-id="d3f4f-153">[공유 데이터 집합 관리](report-data/manage-shared-datasets.md) </span><span class="sxs-lookup"><span data-stu-id="d3f4f-153">[Manage Shared Datasets](report-data/manage-shared-datasets.md) </span></span>  
 [<span data-ttu-id="d3f4f-154">공유 데이터 세트 캐시&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d3f4f-154">Cache Shared Datasets &#40;SSRS&#41;</span></span>](report-server/cache-shared-datasets-ssrs.md)  
  
  

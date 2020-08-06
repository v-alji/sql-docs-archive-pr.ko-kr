---
title: 데이터 프로파일링 태스크 편집기(일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataprofilingtask.general.f1
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: eec15906-d757-4079-b2f6-aca4e52b3b4c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4cfcdf472f817d3dd688a5f867ac74d46835ab91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652261"
---
# <a name="data-profiling-task-editor-general-page"></a><span data-ttu-id="297cb-102">데이터 프로파일링 태스크 편집기(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="297cb-102">Data Profiling Task Editor (General Page)</span></span>
  <span data-ttu-id="297cb-103">**데이터 프로파일링 태스크 편집기** 의 **일반** 페이지를 사용하여 다음 옵션을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-103">Use the **General** page of the **Data Profiling Task Editor** to configure the following options:</span></span>  
  
-   <span data-ttu-id="297cb-104">프로필 출력의 대상을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-104">Specify the destination for the profile output.</span></span>  
  
-   <span data-ttu-id="297cb-105">기본 설정을 사용하여 단일 테이블 또는 뷰를 프로파일링하는 태스크를 단순화합니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-105">Use the default settings to simplify the task of profiling a single table or view.</span></span>  
  
 <span data-ttu-id="297cb-106">데이터 프로파일링 태스크를 사용하는 방법에 대한 자세한 내용은 [데이터 프로파일링 태스크 설정](data-profiling-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="297cb-106">For more information about how to use the Data Profiling task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="297cb-107">데이터 프로필 뷰어를 사용하여 데이터 프로파일링 태스크의 출력을 분석하는 방법에 대한 자세한 내용은 [데이터 프로필 뷰어](data-profile-viewer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="297cb-107">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
 <span data-ttu-id="297cb-108">**데이터 프로파일링 태스크 편집기의 일반 페이지를 열려면**</span><span class="sxs-lookup"><span data-stu-id="297cb-108">**To open the General page of the Data Profiling Task Editor**</span></span>  
  
1.  <span data-ttu-id="297cb-109">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 데이터 프로파일링 태스크가 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that has the Data Profiling task.</span></span>  
  
2.  <span data-ttu-id="297cb-110">**제어 흐름** 탭에서 데이터 프로파일링 태스크를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-110">On the **Control Flow** tab, double-click the Data Profiling task.</span></span>  
  
3.  <span data-ttu-id="297cb-111">**데이터 프로파일링 태스크 편집기**에서 **일반**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-111">In the **Data Profiling Task Editor**, click **General**.</span></span>  
  
## <a name="data-profiling-options"></a><span data-ttu-id="297cb-112">데이터 프로파일링 옵션</span><span class="sxs-lookup"><span data-stu-id="297cb-112">Data Profiling Options</span></span>  
 <span data-ttu-id="297cb-113">**Timeout**</span><span class="sxs-lookup"><span data-stu-id="297cb-113">**Timeout**</span></span>  
 <span data-ttu-id="297cb-114">데이터 프로파일링 태스크가 시간 초과되어 실행이 중지되는 시간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-114">Specify the number of seconds after which the Data Profiling task should timeout and stop running.</span></span> <span data-ttu-id="297cb-115">기본값은 0으로 제한 시간이 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-115">The default value is 0, which indicates no timeout.</span></span>  
  
## <a name="destination-options"></a><span data-ttu-id="297cb-116">대상 옵션</span><span class="sxs-lookup"><span data-stu-id="297cb-116">Destination Options</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="297cb-117">출력 파일에는 데이터베이스와 해당 데이터베이스에 포함된 데이터에 대한 중요 데이터가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-117">The output file might contain sensitive data about your database and the data that database contains.</span></span> <span data-ttu-id="297cb-118">이 파일을 보다 안전하게 보호하는 방법에 대한 제안 사항은 [패키지에서 사용되는 파일 액세스](../access-to-files-used-by-packages.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="297cb-118">For suggestions about how to make this file more secure, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
 <span data-ttu-id="297cb-119">**DestinationType**</span><span class="sxs-lookup"><span data-stu-id="297cb-119">**DestinationType**</span></span>  
 <span data-ttu-id="297cb-120">데이터 프로필 출력을 파일이나 변수에 저장할 것인지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-120">Specify whether to save the data profile output to a file or a variable:</span></span>  
  
|<span data-ttu-id="297cb-121">값</span><span class="sxs-lookup"><span data-stu-id="297cb-121">Value</span></span>|<span data-ttu-id="297cb-122">Description</span><span class="sxs-lookup"><span data-stu-id="297cb-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="297cb-123">**FileConnection**</span><span class="sxs-lookup"><span data-stu-id="297cb-123">**FileConnection**</span></span>|<span data-ttu-id="297cb-124">파일 연결 관리자에서 지정한 위치에 있는 파일에 프로필 출력을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-124">Save the profile output to a file in the location that is specified in a File connection manager.</span></span><br /><br /> <span data-ttu-id="297cb-125">참고: **Destination** 옵션에서 사용할 파일 연결 관리자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-125">Note: You specify which File connection manager to use in the **Destination** option.</span></span>|  
|<span data-ttu-id="297cb-126">**변수**</span><span class="sxs-lookup"><span data-stu-id="297cb-126">**Variable**</span></span>|<span data-ttu-id="297cb-127">프로필 출력을 패키지 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-127">Save the profile output to a package variable.</span></span><br /><br /> <span data-ttu-id="297cb-128">참고: **Destination** 옵션에서 사용할 패키지 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-128">Note: You specify which package variable to use in the **Destination** option.</span></span>|  
  
 <span data-ttu-id="297cb-129">**대상**</span><span class="sxs-lookup"><span data-stu-id="297cb-129">**Destination**</span></span>  
 <span data-ttu-id="297cb-130">데이터 프로필 출력을 포함할 파일 연결 관리자 또는 패키지 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-130">Specify which File connection manager or package variable contains the data profile output:</span></span>  
  
-   <span data-ttu-id="297cb-131">**DestinationType** 옵션이 **FileConnection**으로 설정된 경우 **Destination** 옵션에 사용 가능한 파일 연결 관리자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-131">If the **DestinationType** option is set to **FileConnection**, the **Destination** option displays the available File connection managers.</span></span> <span data-ttu-id="297cb-132">이러한 연결 관리자 중 하나를 선택하거나 \<New File connection>을 선택하여 새 파일 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-132">Select one of these connection managers, or select \<New File connection> to create a new File connection manager.</span></span>  
  
-   <span data-ttu-id="297cb-133">**DestinationType** 옵션이 **Variable**로 설정된 경우 **Destination** 옵션에 사용 가능한 패키지 변수가 **Destination** 목록으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-133">If the **DestinationType** option is set to **Variable**, the **Destination** option displays the available package variables in the **Destination** list.</span></span> <span data-ttu-id="297cb-134">이러한 변수 중 하나를 선택하거나 \<New Variable>를 선택하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-134">Select one of these variables, or select \<New Variable> to create a new variable.</span></span>  
  
 <span data-ttu-id="297cb-135">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="297cb-135">**OverwriteDestination**</span></span>  
 <span data-ttu-id="297cb-136">출력 파일이 이미 있는 경우 덮어쓸 것인지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-136">Specify whether to overwrite the output file if it already exists.</span></span> <span data-ttu-id="297cb-137">기본값은 **False**입니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-137">The default value is **False**.</span></span> <span data-ttu-id="297cb-138">이 속성의 값은 DestinationType 옵션이 FileConnection으로 설정된 경우에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-138">The value of this property is used only when the DestinationType option is set to FileConnection.</span></span> <span data-ttu-id="297cb-139">DestinationType 옵션이 Variable로 설정된 경우 태스크에서는 변수의 이전 값을 항상 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-139">When the DestinationType option is set to Variable, the task always overwrites the previous value of the variable.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="297cb-140">출력 파일 이름을 바꾸거나 **OverwriteDestination** 속성의 값을 **True**로 변경하지 않고 데이터 프로파일링 태스크를 두 번 이상 실행하려고 하면 출력 파일이 이미 있다는 메시지와 함께 태스크가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-140">If you try to run the Data Profiling task more than once without changing the output file name or changing the value of the **OverwriteDestination** property to **True**, the task fails with the message that the output file already exists.</span></span>  
  
## <a name="other-options"></a><span data-ttu-id="297cb-141">다른 옵션</span><span class="sxs-lookup"><span data-stu-id="297cb-141">Other Options</span></span>  
 <span data-ttu-id="297cb-142">**빠른 프로필**</span><span class="sxs-lookup"><span data-stu-id="297cb-142">**Quick Profile**</span></span>  
 <span data-ttu-id="297cb-143">**단일 테이블 빠른 프로필 형식**을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-143">Display the **Single Table Quick Profile Form**.</span></span> <span data-ttu-id="297cb-144">이 형식은 기본 설정을 사용하여 단일 테이블 또는 뷰를 프로파일링하는 태스크를 단순화합니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-144">This form simplifies the task of profiling a single table or view by using default settings.</span></span> <span data-ttu-id="297cb-145">자세한 내용은 [단일 테이블 빠른 프로필 형식&#40;데이터 프로파일링 태스크&#41;](single-table-quick-profile-form-data-profiling-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="297cb-145">For more information, see [Single Table Quick Profile Form &#40;Data Profiling Task&#41;](single-table-quick-profile-form-data-profiling-task.md).</span></span>  
  
 <span data-ttu-id="297cb-146">**프로필 뷰어 열기**</span><span class="sxs-lookup"><span data-stu-id="297cb-146">**Open Profile Viewer**</span></span>  
 <span data-ttu-id="297cb-147">데이터 프로필 뷰어를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-147">Opens the Data Profile Viewer.</span></span> <span data-ttu-id="297cb-148">독립 실행형 데이터 프로필 뷰어에는 데이터 프로파일링 태스크의 데이터 프로필 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-148">The stand-alone Data Profile Viewer displays data profile output from the Data Profiling task.</span></span> <span data-ttu-id="297cb-149">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지 내에서 데이터 프로파일링 태스크를 실행하고 데이터 프로필을 계산한 후에 이러한 프로필 출력을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-149">You can view the data profile output after you have run the Data Profiling task inside the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package and computed the data profiles.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="297cb-150">*\<drive>* :\Program Files (x86) | Program Files\Microsoft SQL Server\110\DTS\Binn 폴더에서 DataProfileViewer.exe를 실행하여 데이터 프로필 뷰어를 열 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="297cb-150">You can also open the Data Profile Viewer by running the DataProfileViewer.exe in the folder, *\<drive>*:\Program Files (x86) | Program Files\Microsoft SQL Server\110\DTS\Binn.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="297cb-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="297cb-151">See Also</span></span>  
 <span data-ttu-id="297cb-152">[단일 테이블 빠른 프로필 형식&#40;데이터 프로파일링 태스크&#41;](single-table-quick-profile-form-data-profiling-task.md) </span><span class="sxs-lookup"><span data-stu-id="297cb-152">[Single Table Quick Profile Form &#40;Data Profiling Task&#41;](single-table-quick-profile-form-data-profiling-task.md) </span></span>  
 [<span data-ttu-id="297cb-153">데이터 프로파일링 태스크 편집기&#40;프로필 요청 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="297cb-153">Data Profiling Task Editor &#40;Profile Requests Page&#41;</span></span>](data-profiling-task-editor-profile-requests-page.md)  
  
  

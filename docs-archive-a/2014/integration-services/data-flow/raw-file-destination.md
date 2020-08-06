---
title: 원시 파일 대상 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rawfiledest.f1
helpviewer_keywords:
- append options [Integration Services]
- destinations [Integration Services], Raw File
- raw data [Integration Services]
- writing raw data
- Raw File destination
ms.assetid: d311b458-aefc-4b4d-b1a1-4c0ebbb34214
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fc5ce99be6e467ba323137ef885cbb13bfb328ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648460"
---
# <a name="raw-file-destination"></a><span data-ttu-id="cf194-102">Raw File Destination</span><span class="sxs-lookup"><span data-stu-id="cf194-102">Raw File Destination</span></span>
  <span data-ttu-id="cf194-103">원시 파일 대상은 원시 데이터를 파일에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-103">The Raw File destination writes raw data to a file.</span></span> <span data-ttu-id="cf194-104">대상의 기본 데이터 형식을 사용하므로 데이터를 변환하거나 구문 분석할 필요도 거의 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-104">Because the format of the data is native to the destination, the data requires no translation and little parsing.</span></span> <span data-ttu-id="cf194-105">따라서 원시 파일 대상은 플랫 파일 및 OLE DB 대상과 같은 다른 대상보다 빨리 데이터를 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-105">This means that the Raw File destination can write data more quickly than other destinations such as the Flat File and the OLE DB destinations.</span></span>  
  
 <span data-ttu-id="cf194-106">원시 데이터를 파일에 기록하는 것 외에도 패키지를 실행할 필요 없이 원시 파일 대상을 사용하여 열만 포함된 비어 있는 원시 파일(메타데이터 전용 파일)을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-106">In addition to writing raw data to a file, you can also use the Raw File destination to generate an empty raw file that contains only the columns (metadata-only file), without having to run the package.</span></span> <span data-ttu-id="cf194-107">원시 파일 원본을 사용하면 대상이 이전에 기록한 원시 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-107">You use the Raw File source to retrieve raw data that was previously written by the destination.</span></span> <span data-ttu-id="cf194-108">또한 원시 파일 원본이 메타데이터 전용 파일을 가리키도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-108">You can also point the Raw File source to the metadata-only file.</span></span>  
  
 <span data-ttu-id="cf194-109">원시 파일 서식에는 정렬 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-109">The raw file format contains sort information.</span></span> <span data-ttu-id="cf194-110">원시 파일 대상에는 문자열 열을 위한 비교 플래그를 포함하여 모든 정렬 정보가 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-110">The Raw File Destination saves all the sort information including the comparison flags for string columns.</span></span> <span data-ttu-id="cf194-111">원시 파일 원본은 정렬 정보를 읽고 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-111">The Raw File source reads and honors the sort information.</span></span> <span data-ttu-id="cf194-112">고급 편집기를 사용하면 파일의 정렬 플래그를 무시하도록 원시 파일 원본을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-112">You do have the option of configuring the Raw File Source to ignore the sort flags in the file, using the Advanced Editor.</span></span> <span data-ttu-id="cf194-113">비교 플래그에 대한 자세한 내용은 [Comparing String Data](comparing-string-data.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="cf194-113">For more information about comparison flags, see [Comparing String Data](comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="cf194-114">다음과 같은 방법으로 원시 파일 대상을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-114">You can configure the Raw File destination in the following ways:</span></span>  
  
-   <span data-ttu-id="cf194-115">원시 파일 대상이 기록할 파일 이름 또는 파일 이름이 포함된 변수인 액세스 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-115">Specify an access mode which is either the name of the file or a variable that contains the name of the file to which the Raw File destination writes.</span></span>  
  
-   <span data-ttu-id="cf194-116">원시 파일 대상이 같은 이름의 기존 파일에 데이터를 추가할지 아니면 새 파일을 만들지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-116">Indicate whether the Raw File destination appends data to an existing file that has the same name or creates a new file.</span></span>  
  
 <span data-ttu-id="cf194-117">원시 파일 대상은 패키지 실행 사이에 부분적으로 처리된 데이터의 결과를 즉시 기록하는 데 자주 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-117">The Raw File destination is frequently used to write intermediary results of partly processed data between package executions.</span></span> <span data-ttu-id="cf194-118">원시 데이터를 저장하면 원시 파일 원본에서 데이터를 신속하게 읽고 최종 대상에 로드되기 전에 추가 변환을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-118">Storing raw data means that the data can be read quickly by a Raw File source and then further transformed before it is loaded into its final destination.</span></span> <span data-ttu-id="cf194-119">예를 들어 패키지를 여러 번 실행하고 이 때마다 원시 데이터를 파일에 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-119">For example, a package might run several times, and each time write raw data to files.</span></span> <span data-ttu-id="cf194-120">그런 다음에는 다른 패키지에서 원시 파일 원본을 사용하여 각 파일에서 데이터를 읽고, UNION ALL 변환을 사용하여 데이터를 하나의 데이터 집합으로 병합한 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블과 같은 최종 대상으로 데이터를 로드하기 전에 데이터를 요약하는 추가 변환을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-120">Later, a different package can use the Raw File source to read from each file, use a Union All transformation to merge the data into one data set, and then apply additional transformations that summarize the data before loading the data into its final destination such as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cf194-121">원시 파일 대상은 BLOB(Binary Large Object) 데이터를 제외한 Null 데이터를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-121">The Raw File destination supports null data but not binary large object (BLOB) data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cf194-122">원시 파일 대상에는 연결 관리자가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-122">The Raw File destination does not use a connection manager.</span></span>  
  
 <span data-ttu-id="cf194-123">이 원본에는 하나의 일반 입력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-123">This source has one regular input.</span></span> <span data-ttu-id="cf194-124">오류 출력은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-124">It does not support an error output.</span></span>  
  
## <a name="append-and-new-file-options"></a><span data-ttu-id="cf194-125">추가 및 새 파일 옵션</span><span class="sxs-lookup"><span data-stu-id="cf194-125">Append and New File Options</span></span>  
 <span data-ttu-id="cf194-126">WriteOption 속성에는 기존 파일에 데이터를 추가하거나 새 파일을 만드는 옵션이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-126">The WriteOption property includes options to append data to an existing file or create a new file.</span></span>  
  
 <span data-ttu-id="cf194-127">다음 표에서는 WriteOption 속성에서 사용할 수 있는 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-127">The following table describes the available options for the WriteOption property.</span></span>  
  
|<span data-ttu-id="cf194-128">옵션</span><span class="sxs-lookup"><span data-stu-id="cf194-128">Option</span></span>|<span data-ttu-id="cf194-129">Description</span><span class="sxs-lookup"><span data-stu-id="cf194-129">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="cf194-130">추가</span><span class="sxs-lookup"><span data-stu-id="cf194-130">Append</span></span>|<span data-ttu-id="cf194-131">기존 파일에 데이터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-131">Appends data to an existing file.</span></span> <span data-ttu-id="cf194-132">추가된 데이터의 메타데이터가 해당 파일 형식과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-132">The metadata of the appended data must match the file format.</span></span>|  
|<span data-ttu-id="cf194-133">항상 만들기</span><span class="sxs-lookup"><span data-stu-id="cf194-133">Create always</span></span>|<span data-ttu-id="cf194-134">항상 새 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-134">Always creates a new file.</span></span>|  
|<span data-ttu-id="cf194-135">한 번 만들기</span><span class="sxs-lookup"><span data-stu-id="cf194-135">Create once</span></span>|<span data-ttu-id="cf194-136">새 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-136">Creates a new file.</span></span> <span data-ttu-id="cf194-137">파일이 있는 경우 구성 요소가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-137">If the file exists, the component fails.</span></span>|  
|<span data-ttu-id="cf194-138">잘라내기 및 추가</span><span class="sxs-lookup"><span data-stu-id="cf194-138">Truncate and append</span></span>|<span data-ttu-id="cf194-139">기존 파일을 잘라낸 다음 데이터를 파일에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-139">Truncates an existing file and then writes the data to the file.</span></span> <span data-ttu-id="cf194-140">추가된 데이터의 메타데이터가 해당 파일 형식과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-140">The metadata of the appended data must match the file format.</span></span>|  
  
 <span data-ttu-id="cf194-141">다음은 데이터 추가와 관련된 중요한 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-141">The following are important items about appending data:</span></span>  
  
-   <span data-ttu-id="cf194-142">기존 원시 파일에 데이터를 추가해도 데이터가 다시 정렬되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-142">Appending data to an existing raw file does not re-sort the data.</span></span>  
  
     <span data-ttu-id="cf194-143">정렬된 키가 올바른 순서인지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-143">You need to make certain that the sorted keys remain in the correct order.</span></span>  
  
-   <span data-ttu-id="cf194-144">기존 원시 파일에 데이터를 추가해도 파일 메타데이터(정렬 정보)는 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-144">Appending data to an existing raw file does not change the file metadata (sort information).</span></span>  
  
 <span data-ttu-id="cf194-145">예를 들어 패키지는 ProductKey(PK)로 정렬된 데이터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-145">For example, a package reads data sorted on the ProductKey (PK).</span></span> <span data-ttu-id="cf194-146">패키지 데이터 흐름은 데이터를 기존 원시 파일에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-146">The package data flow appends the data to an existing raw file.</span></span> <span data-ttu-id="cf194-147">패키지를 처음 실행하면 PK 1000, 1100, 1200의 세 개 행이 수신됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-147">The first time the package runs, three rows are received (PK 1000, 1100, 1200).</span></span> <span data-ttu-id="cf194-148">원시 파일에는 이제 다음과 같은 데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-148">The raw file now contains the following data.</span></span>  
  
-   <span data-ttu-id="cf194-149">1000, productA</span><span class="sxs-lookup"><span data-stu-id="cf194-149">1000, productA</span></span>  
  
-   <span data-ttu-id="cf194-150">1100, productB</span><span class="sxs-lookup"><span data-stu-id="cf194-150">1100, productB</span></span>  
  
-   <span data-ttu-id="cf194-151">1200, productC</span><span class="sxs-lookup"><span data-stu-id="cf194-151">1200, productC</span></span>  
  
 <span data-ttu-id="cf194-152">패키지를 두 번째로 실행하면 PK 1001, 1300의 새로운 두 행이 수신됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-152">The second time the package runs, two new rows are received (PK 1001, 1300).</span></span> <span data-ttu-id="cf194-153">원시 파일에는 이제 다음과 같은 데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-153">The raw file now contains the following data.</span></span>  
  
-   <span data-ttu-id="cf194-154">1000, productA</span><span class="sxs-lookup"><span data-stu-id="cf194-154">1000, productA</span></span>  
  
-   <span data-ttu-id="cf194-155">1100, productB</span><span class="sxs-lookup"><span data-stu-id="cf194-155">1100, productB</span></span>  
  
-   <span data-ttu-id="cf194-156">1200, productC</span><span class="sxs-lookup"><span data-stu-id="cf194-156">1200, productC</span></span>  
  
-   <span data-ttu-id="cf194-157">1001, productD</span><span class="sxs-lookup"><span data-stu-id="cf194-157">1001, productD</span></span>  
  
-   <span data-ttu-id="cf194-158">1300, productE</span><span class="sxs-lookup"><span data-stu-id="cf194-158">1300, productE</span></span>  
  
 <span data-ttu-id="cf194-159">새 데이터가 원시 파일의 끝에 추가되고 정렬된 키(PK)의 순서가 뒤섞입니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-159">The new data is appended to the end of the raw file, and the sorted keys (PK) are out of order.</span></span> <span data-ttu-id="cf194-160">또한 추가 작업으로 파일 메타데이터(정렬 정보)는 변경되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-160">In addition, the append operation didn't change the file metadata (sort information).</span></span> <span data-ttu-id="cf194-161">원시 파일 원본을 사용하여 이 파일을 읽으면 이 파일의 데이터가 더 이상 올바른 순서가 아니더라도 구성 요소에 이 파일이 여전히 PK로 정렬된 것으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-161">If you read the file by using the Raw File source, the component indicates that the file is still sorted on PK even though the data in the file is no longer in the correct order.</span></span>  
  
 <span data-ttu-id="cf194-162">데이터를 추가할 때 정렬된 키를 올바른 순서로 유지하기 위해서는 패키지 데이터 흐름을 다음과 같이 디자인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-162">To keep the sorted keys in the correct order while appending data, you can design the package data flow as follows:</span></span>  
  
1.  <span data-ttu-id="cf194-163">원본 A를 사용하여 새 행을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-163">Retrieve new rows by using Source A.</span></span>  
  
2.  <span data-ttu-id="cf194-164">원본 B를 사용하여 RawFile1에서 기존 행을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-164">Retrieve existing rows from RawFile1 using Source B.</span></span>  
  
3.  <span data-ttu-id="cf194-165">UNION ALL 변환을 사용하여 원본 A와 원본 B의 입력을 조합합니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-165">Combine the inputs from Source A and Source B by using the Union All transformation.</span></span>  
  
4.  <span data-ttu-id="cf194-166">PK로 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-166">Sort on PK.</span></span>  
  
5.  <span data-ttu-id="cf194-167">원시 파일 대상을 사용하여 RawFile2에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-167">Write to RawFile2 by using the Raw File destination.</span></span>  
  
     <span data-ttu-id="cf194-168">RawFile1은 데이터 흐름에서 읽는 중이므로 잠겨 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-168">RawFile1 is locked because it's being read from, in the data flow.</span></span>  
  
6.  <span data-ttu-id="cf194-169">RawFile1을 RawFile2로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-169">Replace RawFile1 with RawFile2.</span></span>  
  
### <a name="using-the-raw-file-destination-in-a-loop"></a><span data-ttu-id="cf194-170">루프에서 원시 파일 대상 사용</span><span class="sxs-lookup"><span data-stu-id="cf194-170">Using the Raw File Destination in a Loop</span></span>  
 <span data-ttu-id="cf194-171">원시 파일 대상을 사용하는 데이터 흐름이 루프에 있는 경우 파일을 한 번만 만들고 루프가 반복되면 파일에 데이터를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-171">If the data flow that uses the Raw File destination is in a loop, you may want to create the file once and then append data to the file when the loop repeats.</span></span> <span data-ttu-id="cf194-172">파일에 데이터를 추가하려면 추가되는 데이터는 기존 파일의 형식과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-172">To append data to the file, the data that is appended must match the format of the existing file.</span></span>  
  
 <span data-ttu-id="cf194-173">루프의 첫 번째 반복에서 파일을 만든 다음 루프의 후속 반복에서 행을 추가하려면 디자인 타임에 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-173">To create the file in the first iteration of the loop, and then append rows in the subsequent iterations of the loop, you need to do the following at design time:</span></span>  
  
1.  <span data-ttu-id="cf194-174">WriteOption 속성을 **CreateOnce** 또는 **CreateAlways**로 설정하고 루프의 반복 하나를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-174">Set the WriteOption property to **CreateOnce** or **CreateAlways**and run one iteration of the loop.</span></span> <span data-ttu-id="cf194-175">파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-175">The file is created.</span></span> <span data-ttu-id="cf194-176">이렇게 하면 추가된 데이터와 파일의 메타데이터가 일치하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-176">This ensures that the metadata of appended data and the file matches.</span></span>  
  
2.  <span data-ttu-id="cf194-177">WriteOption 속성을 **Append** 로 다시 설정 하 고 ValidateExternalMetadata 속성을로 설정 합니다 `False` .</span><span class="sxs-lookup"><span data-stu-id="cf194-177">Reset the WriteOption property to **Append** and set the ValidateExternalMetadata property to `False`.</span></span>  
  
 <span data-ttu-id="cf194-178">**Append** 옵션 대신에 **TruncateAppend** 옵션을 사용할 경우 이전 반복에서 추가된 행이 잘리고 새 행이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-178">If you use the **TruncateAppend** option instead of the **Append** option, it will truncate rows that were added in any previous iteration, and then append new rows.</span></span> <span data-ttu-id="cf194-179">**TruncateAppend** 옵션을 사용할 경우에도 데이터가 파일 형식과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-179">Using the **TruncateAppend** option also requires that the data matches the file format.</span></span>  
  
## <a name="configuration-of-the-raw-file-destination"></a><span data-ttu-id="cf194-180">원시 파일 대상 구성</span><span class="sxs-lookup"><span data-stu-id="cf194-180">Configuration of the Raw File Destination</span></span>  
 <span data-ttu-id="cf194-181">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-181">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="cf194-182">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf194-182">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="cf194-183">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="cf194-183">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="cf194-184">Common Properties</span><span class="sxs-lookup"><span data-stu-id="cf194-184">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="cf194-185">원시 파일 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="cf194-185">Raw File Custom Properties</span></span>](raw-file-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="cf194-186">관련 작업</span><span class="sxs-lookup"><span data-stu-id="cf194-186">Related Tasks</span></span>  
 <span data-ttu-id="cf194-187">구성 요소의 속성을 설정하는 방법에 대한 자세한 내용은 [데이터 흐름 구성 요소의 속성 설정](set-the-properties-of-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cf194-187">For information about how to set properties of the component, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="cf194-188">관련 내용</span><span class="sxs-lookup"><span data-stu-id="cf194-188">Related Content</span></span>  
 <span data-ttu-id="cf194-189">sqlservercentral.com의 블로그 항목 - [원시 파일의 놀라운 기능](https://www.sqlservercentral.com/blogs/31-days-of-ssis-%e2%80%93-raw-files-are-awesome-131)</span><span class="sxs-lookup"><span data-stu-id="cf194-189">Blog entry, [Raw Files Are Awesome](https://www.sqlservercentral.com/blogs/31-days-of-ssis-%e2%80%93-raw-files-are-awesome-131), on sqlservercentral.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf194-190">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cf194-190">See Also</span></span>  
 <span data-ttu-id="cf194-191">[원시 파일 원본](raw-file-source.md) </span><span class="sxs-lookup"><span data-stu-id="cf194-191">[Raw File Source](raw-file-source.md) </span></span>  
 [<span data-ttu-id="cf194-192">데이터 흐름</span><span class="sxs-lookup"><span data-stu-id="cf194-192">Data Flow</span></span>](data-flow.md)  
  
  

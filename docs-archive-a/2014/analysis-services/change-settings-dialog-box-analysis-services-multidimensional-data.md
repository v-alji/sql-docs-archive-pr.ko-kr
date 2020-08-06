---
title: 설정 변경 대화 상자 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.batchsettingsdialog.f1
ms.assetid: 0041e042-d7ce-48f9-a690-a6dc65471ff3
author: minewiskan
ms.author: owend
ms.openlocfilehash: e2649195e3aff4e17d378e54c4b1d656361dfe3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648703"
---
# <a name="change-settings-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="6d15b-102">설정 변경 대화 상자(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="6d15b-102">Change Settings Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="6d15b-103">**및** 의 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 설정 변경 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 대화 상자를 사용하여 **처리** 대화 상자에 나열된 개체의 처리를 제어하는 설정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-103">Use the **Change Settings** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to change the settings that govern the processing of objects listed in the **Process** dialog box.</span></span> <span data-ttu-id="6d15b-104">**처리** 대화 상자에서 **설정 변경** 을 클릭하여 **설정 변경** 대화 상자를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-104">You can display the **Change Settings** dialog box by clicking **Change Settings** on the **Process** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6d15b-105"> 이 대화 상자에서 지정한 설정은 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 처리 **대화 상자에 나열된 개체에 대해** 데이터베이스에서 상속된 기본 설정을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-105">Settings specified in this dialog box override default settings inherited from the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database for the objects listed in the **Process** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6d15b-106">옵션</span><span class="sxs-lookup"><span data-stu-id="6d15b-106">Options</span></span>  
 <span data-ttu-id="6d15b-107">**처리 옵션**</span><span class="sxs-lookup"><span data-stu-id="6d15b-107">**Processing options**</span></span>  
 <span data-ttu-id="6d15b-108">이 탭을 사용하여 처리 순서, 쓰기 저장 테이블 및 처리 작업에 영향을 받는 개체와 관련된 설정을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-108">Use this tab to modify settings related to the processing order, writeback table, and affected objects for the processing operation.</span></span> <span data-ttu-id="6d15b-109">탭에는 다음 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-109">The tab contains the following options:</span></span>  
  
 <span data-ttu-id="6d15b-110">**Parallel**</span><span class="sxs-lookup"><span data-stu-id="6d15b-110">**Parallel**</span></span>  
 <span data-ttu-id="6d15b-111">개체를 병렬로 처리하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-111">Click to process the objects in parallel.</span></span>  
  
 <span data-ttu-id="6d15b-112">**최대 병렬 태스크 수**</span><span class="sxs-lookup"><span data-stu-id="6d15b-112">**Maximum parallel tasks**</span></span>  
 <span data-ttu-id="6d15b-113">처리 작업에서 병렬로 실행할 최대 태스크 수를 선택하거나 **서버에서 지정** 을 선택하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서 최적 병렬 작업 수를 선택할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-113">Select the maximum number of tasks to execute in parallel by the processing operation, or choose **Let the server decide** to allow [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to select an optimal number of parallel tasks.</span></span>  
  
 <span data-ttu-id="6d15b-114">**순차**</span><span class="sxs-lookup"><span data-stu-id="6d15b-114">**Sequential**</span></span>  
 <span data-ttu-id="6d15b-115">개체를 순서대로 처리하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-115">Click to process the objects sequentially.</span></span>  
  
 <span data-ttu-id="6d15b-116">**트랜잭션 모드**</span><span class="sxs-lookup"><span data-stu-id="6d15b-116">**Transaction mode**</span></span>  
 <span data-ttu-id="6d15b-117">개체를 순서대로 처리할 때 사용할 트랜잭션 모드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-117">Choose the transaction mode that is used when objects are processed in sequential order:</span></span>  
  
-   <span data-ttu-id="6d15b-118">**단일 트랜잭션** 은 같은 트랜잭션에 있는 모든 개체를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-118">**One Transaction** processes all objects in the same transaction.</span></span>  
  
-   <span data-ttu-id="6d15b-119">**개별 트랜잭션** 은 종속 개체를 포함하여 개별 트랜잭션에 있는 모든 개체를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-119">**Separate Transactions** processes all objects, including dependent objects, in separate transactions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6d15b-120"> 이 옵션은 **순차** 를 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-120">This option is enabled only if **Sequential** is selected.</span></span>  
  
 <span data-ttu-id="6d15b-121">**쓰기 저장 테이블 옵션**</span><span class="sxs-lookup"><span data-stu-id="6d15b-121">**Writeback table option**</span></span>  
 <span data-ttu-id="6d15b-122">쓰기 저장 테이블 관리 시 사용할 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-122">Choose the option used to manage a writeback table:</span></span>  
  
-   <span data-ttu-id="6d15b-123">**만들기** 는 쓰기 저장 테이블이 없을 경우 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-123">**Create** creates a writeback table if it does not exist.</span></span> <span data-ttu-id="6d15b-124">쓰기 저장 테이블이 이미 있으면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-124">An error occurs if a writeback table already exists.</span></span>  
  
-   <span data-ttu-id="6d15b-125">**항상 만들기** 는 쓰기 저장 테이블이 없을 경우 새로 만들거나 쓰기 저장 테이블이 있을 경우 기존 테이블을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-125">**Create always** creates a writeback table if it does not exist, or overwrites the existing writeback table if it does exist.</span></span>  
  
-   <span data-ttu-id="6d15b-126">**기존 테이블 사용** 은 쓰기 저장 테이블이 있을 경우 기존 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-126">**Use existing** uses the existing writeback table if it exists.</span></span> <span data-ttu-id="6d15b-127">쓰기 저장 테이블이 없으면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-127">An error occurs if a writeback table does not exist.</span></span>  
  
 <span data-ttu-id="6d15b-128">**영향을 받는 개체 처리**</span><span class="sxs-lookup"><span data-stu-id="6d15b-128">**Process affected objects**</span></span>  
 <span data-ttu-id="6d15b-129">처리 작업에 포함된 개체에 종속된 개체를 포함하고 처리하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-129">Select to include and process objects that depend on objects included in the processing operation.</span></span>  
  
 <span data-ttu-id="6d15b-130">**차원 키 오류**</span><span class="sxs-lookup"><span data-stu-id="6d15b-130">**Dimension key errors**</span></span>  
 <span data-ttu-id="6d15b-131">이 탭을 사용하여 처리 작업의 오류 구성과 관련된 설정을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-131">Use this tab to modify settings related to the error configuration for the processing operation.</span></span> <span data-ttu-id="6d15b-132">탭에는 다음 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-132">The tab contains the following options:</span></span>  
  
 <span data-ttu-id="6d15b-133">**기본 오류 구성 사용**</span><span class="sxs-lookup"><span data-stu-id="6d15b-133">**Use default error configuration**</span></span>  
 <span data-ttu-id="6d15b-134">처리 작업에 개체의 기본 오류 구성을 사용하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-134">Select to use the default error configuration for objects in the processing operation.</span></span>  
  
 <span data-ttu-id="6d15b-135">**사용자 지정 오류 구성 사용**</span><span class="sxs-lookup"><span data-stu-id="6d15b-135">**Use custom error configuration**</span></span>  
 <span data-ttu-id="6d15b-136">처리 작업에 포함된 개체의 오류 구성을 정의하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-136">Select to define the error configuration for objects in the processing operation.</span></span>  
  
 <span data-ttu-id="6d15b-137">**키 오류 동작**</span><span class="sxs-lookup"><span data-stu-id="6d15b-137">**Key error action**</span></span>  
 <span data-ttu-id="6d15b-138">처리 중 조회할 수 없는 새 키를 발견할 경우 다음 중에서 수행할 동작을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-138">Choose one of the following actions that occur when a new key is encountered during processing that cannot be looked up:</span></span>  
  
-   <span data-ttu-id="6d15b-139">**알 수 없음 상태로 변환** 은 레코드 정보를 알 수 없는 멤버로 집계합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-139">**Convert to unknown** aggregates the information for the record into the unknown member.</span></span>  
  
-   <span data-ttu-id="6d15b-140">**레코드 삭제** 는 레코드 정보가 개체와 함께 처리되지 않도록 제외합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-140">**Discard record** excludes the information for the record from being processed with the object.</span></span>  
  
 <span data-ttu-id="6d15b-141">**오류 개수 무시**</span><span class="sxs-lookup"><span data-stu-id="6d15b-141">**Ignore errors count**</span></span>  
 <span data-ttu-id="6d15b-142">처리 중 발생한 오류를 무시하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-142">Click to ignore any errors that occur when processing.</span></span>  
  
 <span data-ttu-id="6d15b-143">**오류 발생 시 중지**</span><span class="sxs-lookup"><span data-stu-id="6d15b-143">**Stop on error**</span></span>  
 <span data-ttu-id="6d15b-144">오류 발생 시 처리를 중지하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-144">Click to stop processing when errors occur.</span></span> <span data-ttu-id="6d15b-145">이 옵션을 사용하면 **오류 개수** 및 **오류 시 수행할 동작** 옵션이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-145">This option enables the **Number of errors** and the **On error action** options.</span></span>  
  
 <span data-ttu-id="6d15b-146">**오류 개수**</span><span class="sxs-lookup"><span data-stu-id="6d15b-146">**Number of errors**</span></span>  
 <span data-ttu-id="6d15b-147">처리를 중지할 때까지 무시할 오류 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-147">Type the number of errors that are ignored before processing stops.</span></span>  
  
 <span data-ttu-id="6d15b-148">**오류 시 수행할 동작**</span><span class="sxs-lookup"><span data-stu-id="6d15b-148">**On error action**</span></span>  
 <span data-ttu-id="6d15b-149">다음 동작 중에서 오류 수가 **오류 개수**의 값을 초과할 경우 수행할 작업을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-149">Choose one of the following actions to be taken when the number of errors exceeds the value in **Number of errors**:</span></span>  
  
-   <span data-ttu-id="6d15b-150">**처리 중지** 는 처리 작업을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-150">**Stop processing** ends the processing operation.</span></span>  
  
-   <span data-ttu-id="6d15b-151">**로깅 중지** 는 오류 기록은 중지하지만 처리 작업은 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-151">**Stop logging** stops logging errors, but continues the processing operation.</span></span>  
  
 <span data-ttu-id="6d15b-152">**키를 찾을 수 없는 경우**</span><span class="sxs-lookup"><span data-stu-id="6d15b-152">**Key not found**</span></span>  
 <span data-ttu-id="6d15b-153">다음 동작 중에서 개체 처리 시 키가 없을 경우 수행할 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-153">Specify one of the following actions to be taken when a key is not found when an object is processed:</span></span>  
  
-   <span data-ttu-id="6d15b-154">**오류 무시** 는 오류를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-154">**Ignore error** ignores the error.</span></span>  
  
-   <span data-ttu-id="6d15b-155">**보고하고 계속** 은 오류를 보고하고 처리 작업을 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-155">**Report and continue** reports the error and continues the processing operation.</span></span>  
  
-   <span data-ttu-id="6d15b-156">**보고하고 중지** 는 오류를 보고하고 처리 작업을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-156">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="6d15b-157">**중복 키**</span><span class="sxs-lookup"><span data-stu-id="6d15b-157">**Duplicate key**</span></span>  
 <span data-ttu-id="6d15b-158">다음 동작 중에서 개체 처리 시 중복 키가 있을 경우 수행할 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-158">Specify one of the following actions to be taken if a duplicate key is found when an object is processed:</span></span>  
  
-   <span data-ttu-id="6d15b-159">**오류 무시** 는 오류를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-159">**Ignore error** ignores the error.</span></span>  
  
-   <span data-ttu-id="6d15b-160">**보고하고 계속** 은 오류를 보고하고 처리 작업을 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-160">**Report and continue** reports the error and continues the processing operation.</span></span>  
  
-   <span data-ttu-id="6d15b-161">**보고하고 중지** 는 오류를 보고하고 처리 작업을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-161">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="6d15b-162">**Null 키가 알 수 없음으로 변환 되었습니다.**</span><span class="sxs-lookup"><span data-stu-id="6d15b-162">**Null key converted to unknown**</span></span>  
 <span data-ttu-id="6d15b-163">다음 동작 중에서 개체 처리 시 Null 멤버 키가 알 수 없는 멤버에 추가될 경우 수행할 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-163">Specify one of the following actions to be taken when a null member key is added to the unknown member when an object is processed:</span></span>  
  
-   <span data-ttu-id="6d15b-164">**오류 무시** 는 오류를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-164">**Ignore error** ignores the error.</span></span>  
  
-   <span data-ttu-id="6d15b-165">**보고하고 계속** 은 오류를 보고하고 처리 작업을 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-165">**Report and continue** reports the error and continues the processing operation.</span></span>  
  
-   <span data-ttu-id="6d15b-166">**보고하고 중지** 는 오류를 보고하고 처리 작업을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-166">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="6d15b-167">**Null 키가 허용 되지 않습니다.**</span><span class="sxs-lookup"><span data-stu-id="6d15b-167">**Null key not allowed**</span></span>  
 <span data-ttu-id="6d15b-168">다음 동작 중에서 개체 처리 시 Null 키를 찾았지만 허용되지 않을 경우 수행할 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-168">Specify one of the following actions to be taken when a null key is found, but not allowed, when an object is processed:</span></span>  
  
-   <span data-ttu-id="6d15b-169">**오류 무시** 는 오류를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-169">**Ignore error** ignores the error.</span></span>  
  
-   <span data-ttu-id="6d15b-170">**보고하고 계속** 은 오류를 보고하고 처리 작업을 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-170">**Report and continue** reports the error and continues the processing operation.</span></span>  
  
-   <span data-ttu-id="6d15b-171">**보고하고 중지** 는 오류를 보고하고 처리 작업을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-171">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="6d15b-172">**오류 로그 경로**</span><span class="sxs-lookup"><span data-stu-id="6d15b-172">**Error log path**</span></span>  
 <span data-ttu-id="6d15b-173">오류 로그 파일의 전체 경로 및 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-173">Type the full path and file name for the error log file.</span></span>  
  
 <span data-ttu-id="6d15b-174">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="6d15b-174">**Browse**</span></span>  
 <span data-ttu-id="6d15b-175">**열기** 대화 상자를 열고 오류 로그 파일의 전체 경로 및 파일 이름을 선택하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-175">Click to open the **Open** dialog box and select the full path and file name for the error log file.</span></span>  
  
 <span data-ttu-id="6d15b-176">**영향을 받는 개체 처리**</span><span class="sxs-lookup"><span data-stu-id="6d15b-176">**Process affected objects**</span></span>  
 <span data-ttu-id="6d15b-177">**처리** 대화 상자에서 선택한 개체에 종속된 개체를 처리하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6d15b-177">Click to process the objects that have a dependency on the objects selected in the **Process** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d15b-178">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6d15b-178">See Also</span></span>  
 <span data-ttu-id="6d15b-179">[Analysis Services 디자이너 및 대화 상자 &#40;다차원 데이터&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="6d15b-179">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="6d15b-180">처리 대화 상자 &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="6d15b-180">Process Dialog Box &#40;Analysis Services - Multidimensional Data&#41;</span></span>](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  

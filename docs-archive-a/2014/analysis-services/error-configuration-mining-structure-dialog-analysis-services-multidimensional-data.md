---
title: 오류 구성 (마이닝 구조 대화 상자) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.miningstructuredialog.general.f1
ms.assetid: d9aa028b-bad9-49c7-a81c-c2150e4dd481
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5eb41da36400271a9b058ecf275d26bd22d3ee53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661393"
---
# <a name="error-configuration-mining-structure-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="c7fe8-102">오류 구성(마이닝 구조 대화 상자)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="c7fe8-102">Error Configuration (Mining Structure Dialog Box) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="c7fe8-103">**SQL Server Management Studio** 의 **마이닝 구조 속성** 대화 상자에 있는 **오류 구성** 페이지를 사용하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스의 마이닝 구조에 대한 오류 구성 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-103">Use the **Error Configuration** page of the **Mining Structure Properties** dialog box in **SQL Server Management Studio** to set the error configuration properties of a mining structure in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c7fe8-104">옵션</span><span class="sxs-lookup"><span data-stu-id="c7fe8-104">Options</span></span>  
 <span data-ttu-id="c7fe8-105">**기본 오류 구성 사용**</span><span class="sxs-lookup"><span data-stu-id="c7fe8-105">**Use default error configuration**</span></span>  
 <span data-ttu-id="c7fe8-106">처리 작업에 개체의 기본 오류 구성을 사용하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-106">Select to use the default error configuration for objects in the processing operation.</span></span>  
  
 <span data-ttu-id="c7fe8-107">**키 오류 동작**</span><span class="sxs-lookup"><span data-stu-id="c7fe8-107">**Key error action**</span></span>  
 <span data-ttu-id="c7fe8-108">처리 중 조회할 수 없는 새 키를 발견할 경우 다음 중에서 수행할 동작을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-108">Choose one of the following actions that occur when a new key is encountered during processing that cannot be looked up:</span></span>  
  
-   <span data-ttu-id="c7fe8-109">**알 수 없음 상태로 변환** 은 레코드 정보를 알 수 없는 멤버로 집계합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-109">**Convert to unknown** aggregates the information for the record into the unknown member.</span></span>  
  
-   <span data-ttu-id="c7fe8-110">**레코드 삭제** 는 레코드 정보가 개체와 함께 처리되지 않도록 제외합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-110">**Discard record** excludes the information for the record from being processed with the object.</span></span>  
  
 <span data-ttu-id="c7fe8-111">**오류 개수 무시**</span><span class="sxs-lookup"><span data-stu-id="c7fe8-111">**Ignore errors count**</span></span>  
 <span data-ttu-id="c7fe8-112">처리 중 발생한 오류를 무시하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-112">Click to ignore any errors that occur when processing.</span></span>  
  
 <span data-ttu-id="c7fe8-113">**오류 발생 시 중지**</span><span class="sxs-lookup"><span data-stu-id="c7fe8-113">**Stop on error**</span></span>  
 <span data-ttu-id="c7fe8-114">오류 발생 시 처리를 중지하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-114">Click to stop processing when errors occur.</span></span> <span data-ttu-id="c7fe8-115">이 옵션을 사용하면 **오류 개수** 및 **오류 시 수행할 동작** 옵션이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-115">This option enables the **Number of errors** and the **On error action** options.</span></span>  
  
 <span data-ttu-id="c7fe8-116">**오류 개수**</span><span class="sxs-lookup"><span data-stu-id="c7fe8-116">**Number of errors**</span></span>  
 <span data-ttu-id="c7fe8-117">처리를 중지할 때까지 무시할 오류 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-117">Type the number of errors that are ignored before processing stops.</span></span>  
  
 <span data-ttu-id="c7fe8-118">**오류 시 수행할 동작**</span><span class="sxs-lookup"><span data-stu-id="c7fe8-118">**On error action**</span></span>  
 <span data-ttu-id="c7fe8-119">다음 동작 중에서 오류 수가 **오류 개수**의 값을 초과할 경우 수행할 작업을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-119">Choose one of the following actions to be taken when the number of errors exceeds the value in **Number of errors**:</span></span>  
  
-   <span data-ttu-id="c7fe8-120">**처리 중지** 는 처리 작업을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-120">**Stop processing** ends the processing operation.</span></span>  
  
-   <span data-ttu-id="c7fe8-121">**로깅 중지** 는 오류 기록은 중지하지만 처리 작업은 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-121">**Stop logging** stops logging errors, but continues the processing operation.</span></span>  
  
 <span data-ttu-id="c7fe8-122">**키를 찾을 수 없는 경우**</span><span class="sxs-lookup"><span data-stu-id="c7fe8-122">**Key not found**</span></span>  
 <span data-ttu-id="c7fe8-123">다음 동작 중에서 개체 처리 시 키가 없을 경우 수행할 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-123">Specify one of the following actions to be taken when a key is not found when an object is processed:</span></span>  
  
-   <span data-ttu-id="c7fe8-124">오류 **무시** 는 오류를 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-124">**Ignore error** ignores the error</span></span>  
  
-   <span data-ttu-id="c7fe8-125">**보고서 및 계속** 에서 오류를 보고 하 고 처리 작업을 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-125">**Report and continue** reports the error and continues the processing operation</span></span>  
  
-   <span data-ttu-id="c7fe8-126">**보고하고 중지** 는 오류를 보고하고 처리 작업을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-126">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="c7fe8-127">**중복 키**</span><span class="sxs-lookup"><span data-stu-id="c7fe8-127">**Duplicate key**</span></span>  
 <span data-ttu-id="c7fe8-128">다음 동작 중에서 개체 처리 시 중복 키가 있을 경우 수행할 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-128">Specify one of the following actions to be taken if a duplicate key is found when an object is processed:</span></span>  
  
-   <span data-ttu-id="c7fe8-129">오류 **무시** 는 오류를 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-129">**Ignore error** ignores the error</span></span>  
  
-   <span data-ttu-id="c7fe8-130">**보고서 및 계속** 에서 오류를 보고 하 고 처리 작업을 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-130">**Report and continue** reports the error and continues the processing operation</span></span>  
  
-   <span data-ttu-id="c7fe8-131">**보고하고 중지** 는 오류를 보고하고 처리 작업을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-131">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="c7fe8-132">**Null 키가 알 수 없음으로 변환 되었습니다.**</span><span class="sxs-lookup"><span data-stu-id="c7fe8-132">**Null key converted to unknown**</span></span>  
 <span data-ttu-id="c7fe8-133">다음 동작 중에서 개체 처리 시 알 수 없는 멤버에 Null 멤버 키를 추가한 경우 수행할 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-133">Specify one of the following actions to be taken when a null member key is added to the unknown member when an object is processed.</span></span>  
  
-   <span data-ttu-id="c7fe8-134">오류 **무시** 는 오류를 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-134">**Ignore error** ignores the error</span></span>  
  
-   <span data-ttu-id="c7fe8-135">**보고서 및 계속** 에서 오류를 보고 하 고 처리 작업을 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-135">**Report and continue** reports the error and continues the processing operation</span></span>  
  
-   <span data-ttu-id="c7fe8-136">**보고하고 중지** 는 오류를 보고하고 처리 작업을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-136">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="c7fe8-137">**Null 키가 허용 되지 않습니다.**</span><span class="sxs-lookup"><span data-stu-id="c7fe8-137">**Null key not allowed**</span></span>  
 <span data-ttu-id="c7fe8-138">다음 동작 중에서 개체 처리 시 허용되지 않는 Null 키를 발견한 경우 수행할 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-138">Specify one of the following actions to be taken when a null key is found, but not allowed, when an object is processed.</span></span>  
  
-   <span data-ttu-id="c7fe8-139">오류 **무시** 는 오류를 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-139">**Ignore error** ignores the error</span></span>  
  
-   <span data-ttu-id="c7fe8-140">**보고서 및 계속** 에서 오류를 보고 하 고 처리 작업을 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-140">**Report and continue** reports the error and continues the processing operation</span></span>  
  
-   <span data-ttu-id="c7fe8-141">**보고하고 중지** 는 오류를 보고하고 처리 작업을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-141">**Report and stop** reports the error and stops the processing operation.</span></span>  
  
 <span data-ttu-id="c7fe8-142">**오류 로그 경로**</span><span class="sxs-lookup"><span data-stu-id="c7fe8-142">**Error log path**</span></span>  
 <span data-ttu-id="c7fe8-143">오류 로그 파일의 전체 경로 및 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c7fe8-143">Type the full path and file name for the error log file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7fe8-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c7fe8-144">See Also</span></span>  
 <span data-ttu-id="c7fe8-145">[마이닝 구조 속성 대화 &#40;Analysis Services 데이터 마이닝&#41;](mining-structure-properties-dialog-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="c7fe8-145">[Mining Structure Properties Dialog &#40;Analysis Services - Data Mining&#41;](mining-structure-properties-dialog-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="c7fe8-146">일반 &#40;마이닝 구조 대화 상자&#41; &#40;Analysis Services 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="c7fe8-146">General &#40;Mining Structure Dialog Box&#41; &#40;Analysis Services - Data Mining&#41;</span></span>](general-mining-structure-dialog-box-analysis-services-data-mining.md)  
  
  

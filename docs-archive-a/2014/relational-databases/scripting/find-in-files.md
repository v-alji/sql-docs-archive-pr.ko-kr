---
title: 파일에서 찾기
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Find in Files dialog box
ms.assetid: bf92770a-33df-43ef-85ad-5a9223649b98
author: rothja
ms.author: jroth
ms.openlocfilehash: a7bd3051817198fb22e2bf7e96393ddf2023b703
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660489"
---
# <a name="find-in-files"></a><span data-ttu-id="55b63-102">파일에서 찾기</span><span class="sxs-lookup"><span data-stu-id="55b63-102">Find in Files</span></span>
  <span data-ttu-id="55b63-103"> 찾기 및 바꾸기 창의 **파일에서 찾기** 탭을 사용하여 지정한 파일에서 문자열이나 식을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-103">The **Find in Files** tab of the Find and Replace window enables you to search the code of a specified set of files for a string or expression.</span></span> <span data-ttu-id="55b63-104">**결과 옵션**에서 선택한 찾기 결과 창에 일치하는 항목과 수행한 동작이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-104">The matches found and actions taken are listed in the Find Results window selected in **Result Options**.</span></span>  
  
 <span data-ttu-id="55b63-105">도구 모음 단추 및 바로 가기 키를 사용하여 **찾기 및 바꾸기** 대화 상자를 열 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-105">Toolbar buttons and shortcut keys are also available to open the **Find and Replace** dialog box.</span></span>  
  
 <span data-ttu-id="55b63-106">다음 섹션에서는 **파일에서 찾기** 탭에서 사용할 수 있는 컨트롤에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-106">The sections that follow list controls available on the **Find in Files** tab.</span></span>  
  
## <a name="find-what"></a><span data-ttu-id="55b63-107">찾을 내용</span><span class="sxs-lookup"><span data-stu-id="55b63-107">Find What</span></span>  
 <span data-ttu-id="55b63-108">**파일에서 찾기** 탭의 이 컨트롤을 사용하여 검색할 문자열 또는 식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-108">These controls on the **Find in Files** tab enable you to specify the string or expression that will be matched.</span></span>  
  
 <span data-ttu-id="55b63-109">**찾을 내용**</span><span class="sxs-lookup"><span data-stu-id="55b63-109">**Find what**</span></span>  
 <span data-ttu-id="55b63-110">검색할 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-110">Type the text to search for.</span></span> <span data-ttu-id="55b63-111">대화 상자에서는 대화 상자를 열기 전에 커서로 선택한 텍스트, 가까이 위치한 텍스트 또는 이전에 검색한 텍스트를 사용하여 가능한 검색 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-111">The dialog box attempts to fill in a probable search text, using text selected with the cursor before opening the dialog box, or nearby text, or previously searched-for text.</span></span> <span data-ttu-id="55b63-112">드롭다운 목록에서 검색 문자열을 선택하여 가장 최근에 사용한 20개의 문자열을 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-112">You can reuse one of the last 20 search strings by selecting it from this drop-down list.</span></span>  
  
 <span data-ttu-id="55b63-113">**[와일드카드가 포함된 문자열]**</span><span class="sxs-lookup"><span data-stu-id="55b63-113">**[string with wildcards]**</span></span>  
 <span data-ttu-id="55b63-114">검색 문자열에 별표(`*`) 및 물음표(`?`)와 같은 와일드카드를 사용하려면 **찾기 옵션** 아래의 **사용** 확인란을 선택한 다음 **와일드카드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-114">If you want to use wildcards such as asterisks (`*`) and question marks (`?`) in your search string, select the **Use** check box under **Find Options** and then click **Wildcards**.</span></span>  
  
 <span data-ttu-id="55b63-115">**[정규식]**</span><span class="sxs-lookup"><span data-stu-id="55b63-115">**[regular expression]**</span></span>  
 <span data-ttu-id="55b63-116">검색 엔진에서 검색 문자열을 정규식으로 해석하려면 **찾기 옵션** 아래의 **사용** 확인란을 선택한 다음 **정규식**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-116">To cause the search engine to interpret your search string as a regular expression, select the **Use** check box under **Find Options** and then click **Regular expressions**.</span></span>  
  
 <span data-ttu-id="55b63-117">**식 작성기**</span><span class="sxs-lookup"><span data-stu-id="55b63-117">**Expression Builder**</span></span>  
 <span data-ttu-id="55b63-118">**찾기 옵션** 에서 **사용** 확인란을 선택하면 **찾을 내용**입력란 옆에 있는 삼각형 단추가 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-118">This triangular button next to the **Find what** box becomes available when the **Use** check box is selected in **Find Options**.</span></span> <span data-ttu-id="55b63-119">이 단추를 클릭하면 선택한 **사용** 옵션에 따라 와일드카드 또는 정규식 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-119">Click this button to display a list of wildcards or regular expressions, depending upon the **Use** option selected.</span></span> <span data-ttu-id="55b63-120">이 목록에서 항목을 선택하면 **찾을 내용** 문자열에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-120">Choosing any item from this list adds it to the **Find what** string.</span></span>  
  
## <a name="look-in"></a><span data-ttu-id="55b63-121">찾는 위치</span><span class="sxs-lookup"><span data-stu-id="55b63-121">Look In</span></span>  
 <span data-ttu-id="55b63-122">**찾는 위치** 드롭다운 목록에서 선택한 옵션에 따라 **파일에서 찾기** 에서 현재 활성화된 파일만 검색할지 아니면 특정 폴더에 저장되어 있는 모든 파일을 검색할지 여부가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-122">The option chosen from the **Look in** drop-down list determines whether **Find in Files** searches only in currently active files or in all files stored within certain folders.</span></span> <span data-ttu-id="55b63-123">목록에서 검색 범위를 선택하거나 폴더 경로를 입력하거나 **찾아보기** 단추를 클릭하여 **사용자 지정 디렉터리 집합** 대화 상자를 표시한 다음 검색할 폴더 집합을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-123">Select a search scope from the list, type a folder path, or click the **Browse** button to display the **Custom Directory Set Dialog Box** and choose a set of folders to search.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="55b63-124">**찾는 위치** 옵션을 선택하면 원본 코드 제어에서 체크 아웃한 파일을 검색합니다. 즉, 로컬 컴퓨터로 다운로드한 버전만 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-124">If the **Look in** option selected causes you to search a file that you have checked out from source code control, only the version of that file which has been downloaded to your local computer is searched.</span></span>  
  
 <span data-ttu-id="55b63-125">**찾는 위치**</span><span class="sxs-lookup"><span data-stu-id="55b63-125">**Look in**</span></span>  
 <span data-ttu-id="55b63-126">이 목록에서 미리 정의된 검색 범위를 선택하거나 **사용자 지정 디렉터리 집합** 대화 상자를 사용하여 원하는 디렉터리 집합을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-126">Select a predefined search scope from this list, or use the **Custom Directory Set** dialog box to enter your own set of directories.</span></span>  
  
 <span data-ttu-id="55b63-127">**현재 문서**</span><span class="sxs-lookup"><span data-stu-id="55b63-127">**Current Document**</span></span>  
 <span data-ttu-id="55b63-128">이 옵션은 편집기에 문서가 열려 있을 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-128">This option is available when a document is open in an editor.</span></span> <span data-ttu-id="55b63-129">이 옵션을 선택하면 활성 문서에서만 **찾을 내용**에 지정된 문자열을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-129">It searches only the active document for the string in **Find what**.</span></span>  
  
 <span data-ttu-id="55b63-130">**모든 열린 문서**</span><span class="sxs-lookup"><span data-stu-id="55b63-130">**All Open Documents**</span></span>  
 <span data-ttu-id="55b63-131">편집하기 위해 현재 열려 있는 모든 파일을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-131">Searches all files currently opened for editing.</span></span>  
  
 <span data-ttu-id="55b63-132">**현재 프로젝트**</span><span class="sxs-lookup"><span data-stu-id="55b63-132">**Current Project**</span></span>  
 <span data-ttu-id="55b63-133">활성 프로젝트에 있는 모든 파일을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-133">Searches all files in the active project.</span></span>  
  
 <span data-ttu-id="55b63-134">**전체 솔루션**</span><span class="sxs-lookup"><span data-stu-id="55b63-134">**Entire Solution**</span></span>  
 <span data-ttu-id="55b63-135">활성 솔루션에 있는 모든 파일을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-135">Searches all files in the active solution.</span></span>  
  
 <span data-ttu-id="55b63-136">**하위 폴더 포함**</span><span class="sxs-lookup"><span data-stu-id="55b63-136">**Include subfolders**</span></span>  
 <span data-ttu-id="55b63-137">**찾는 위치** 에서 지정한 폴더의 하위 폴더도 검색하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-137">Specifies that subfolders of the folder specified in **Look in** will be searched.</span></span> <span data-ttu-id="55b63-138">이 옵션을 사용하려면 사용자 지정 디렉터리 집합이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-138">It requires a custom directory set.</span></span>  
  
 <span data-ttu-id="55b63-139">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="55b63-139">**Browse**</span></span>  
 <span data-ttu-id="55b63-140">이 단추를 클릭하면 **찾는 위치** 상자에 입력할 명명된 디렉터리 집합을 조합, 편집, 저장 및 선택할 수 있는 **사용자 지정 디렉터리 집합** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-140">Click this button to display the **Custom Directory Set** dialog box, where you can assemble, edit, save, and select named sets of directories to enter in the **Look in** box.</span></span>  
  
## <a name="find-options"></a><span data-ttu-id="55b63-141">사용</span><span class="sxs-lookup"><span data-stu-id="55b63-141">Find Options</span></span>  
 <span data-ttu-id="55b63-142">**찾기 옵션** 섹션을 확장하거나 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-142">You can expand or collapse the **Find Options** section.</span></span> <span data-ttu-id="55b63-143">다음과 같은 옵션을 선택하거나 선택 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-143">The following options can be selected or cleared.</span></span>  
  
 <span data-ttu-id="55b63-144">**대/소문자 구분**</span><span class="sxs-lookup"><span data-stu-id="55b63-144">**Match case**</span></span>  
 <span data-ttu-id="55b63-145">이 확인란을 선택하면 찾기 결과 창에 **찾을 내용** 에 지정된 문자열의 인스턴스 중 내용과 대/소문자가 모두 일치하는 인스턴스만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-145">When this check box is selected, the Find Results windows will only display instances of the string specified in **Find what** that are matched both by content and by case.</span></span> <span data-ttu-id="55b63-146">예를 들어 **대/소문자 구분** 확인란을 선택하고 **MyObject** 를 검색하면 "MyObject"는 검색되지만 "myobject" 또는 "MYOBJECT"는 검색되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-146">For example, a search for **MyObject** with the **Match case** check box selected will return "MyObject" but not "myobject" or "MYOBJECT."</span></span>  
  
 <span data-ttu-id="55b63-147">**단어 단위로**</span><span class="sxs-lookup"><span data-stu-id="55b63-147">**Match whole word**</span></span>  
 <span data-ttu-id="55b63-148">이 확인란을 선택하면 **찾을 내용** 에 지정한 문자열과 단어 단위로 일치하는 인스턴스만 찾기 결과 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-148">When this check box is selected, the Find Results windows will only display instances of the string specified in **Find what** that are matched in complete words.</span></span> <span data-ttu-id="55b63-149">예를 들어 **MyObject** 를 검색하면 "MyObject"는 반환되지만 "CMyObject"나 "MyObjectC"는 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-149">For example, a search for **MyObject** will return "MyObject" but not "CMyObject" or "MyObjectC."</span></span>  
  
 <span data-ttu-id="55b63-150">**사용**</span><span class="sxs-lookup"><span data-stu-id="55b63-150">**Use**</span></span>  
 <span data-ttu-id="55b63-151">**찾을 내용** 또는 **바꿀 내용** 입력란에 입력한 특수 문자의 해석 방법을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-151">Indicates how to interpret special characters entered in the **Find what** or **Replace with** text boxes.</span></span> <span data-ttu-id="55b63-152">옵션에는 **와일드카드** 및 **정규식**이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-152">The options include **Wildcards** and **Regular Expressions**.</span></span>  
  
 <span data-ttu-id="55b63-153">**정규식**</span><span class="sxs-lookup"><span data-stu-id="55b63-153">**Regular Expressions**</span></span>  
 <span data-ttu-id="55b63-154">특수 표기를 사용하여 일치하는 텍스트의 패턴을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-154">Special notations define patterns of text to match.</span></span> <span data-ttu-id="55b63-155">목록을 보려면 [정규식으로 텍스트 검색](search-text-with-regular-expressions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="55b63-155">For a list, see [Search Text with Regular Expressions](search-text-with-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="55b63-156">**와일드카드**</span><span class="sxs-lookup"><span data-stu-id="55b63-156">**Wildcards**</span></span>  
 <span data-ttu-id="55b63-157">별표(`*`) 및 물음표(`?`)와 같은 특수 문자는 하나 이상의 문자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-157">Special characters such as asterisks (`*`) and question marks (`?`) represent one or more characters.</span></span> <span data-ttu-id="55b63-158">목록을 보려면 [와일드카드로 텍스트 검색](search-text-with-wildcards.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="55b63-158">For a list, see [Search Text with Wildcards](search-text-with-wildcards.md).</span></span>  
  
 <span data-ttu-id="55b63-159">**이 파일 형식 보기**</span><span class="sxs-lookup"><span data-stu-id="55b63-159">**Look at these file types**</span></span>  
 <span data-ttu-id="55b63-160">이 목록은 **찾는 위치**에 지정한 디렉터리에서 검색할 파일 유형을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-160">This list indicates the types of files to search through in the directories specified in **Look in**.</span></span> <span data-ttu-id="55b63-161">이 필드를 비워 두면 **찾는 위치** 에서 지정한 디렉터리에 있는 모든 파일이 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-161">If this field is left blank, all of the files in the directories specified in **Look in** will be searched.</span></span>  
  
```  
*.[ext]; *.[ext] (manual)  
```  
  
 <span data-ttu-id="55b63-162">특정 유형의 파일을 찾으려면 파일 이름에 별표 와일드카드(`*`)를 입력하고 뒤에 마침표(`.`)와 파일 확장명을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-162">To find files of a particular type, enter an asterisk wildcard (`*`) for the file name, followed by a period (`.`) and the file extension.</span></span> <span data-ttu-id="55b63-163">둘 이상의 파일 유형을 찾으려면 여러 개의 검색 문자열을 세미콜론(`;`)으로 구분하여 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-163">To find more than one file type, enter multiple search strings separated by a semicolon (`;`).</span></span>  
  
```  
*.[ext]; *.[ext] (from list)  
```  
  
 <span data-ttu-id="55b63-164">특정 유형의 파일을 찾는 미리 구성된 검색 문자열을 입력하려면 목록에서 임의 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-164">Select any item in the list to enter a preconfigured search string that will find files of particular types.</span></span>  
  
## <a name="result-options"></a><span data-ttu-id="55b63-165">결과 옵션</span><span class="sxs-lookup"><span data-stu-id="55b63-165">Result Options</span></span>  
 <span data-ttu-id="55b63-166">**모두 찾기**를 클릭했을 때 결과가 표시되는 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-166">Determines the location of the results when you click **Find All**.</span></span> <span data-ttu-id="55b63-167">**결과 옵션** 섹션은 확장하거나 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-167">You can expand or collapse the **Result Options** section.</span></span> <span data-ttu-id="55b63-168">다음과 같은 옵션을 선택하거나 선택 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-168">The following options can be selected or cleared.</span></span>  
  
 <span data-ttu-id="55b63-169">**찾기 결과 1 창**</span><span class="sxs-lookup"><span data-stu-id="55b63-169">**Find Results 1 window**</span></span>  
 <span data-ttu-id="55b63-170">이 확인란을 선택하면 현재 검색 결과가 찾기 결과 1 창의 내용에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-170">When this check box is selected, the results of the current search will be appended to the content of the Find Results 1 window.</span></span> <span data-ttu-id="55b63-171">이 창은 자동으로 열려 검색 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-171">This window opens automatically to display your search results.</span></span> <span data-ttu-id="55b63-172">이 창을 수동으로 열려면 **보기** 메뉴의 **다른 창** 을 클릭한 다음 **찾기 결과 1**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-172">To open this window manually, click **Other Windows** on the **View** menu and then click **Find Results 1**.</span></span>  
  
 <span data-ttu-id="55b63-173">**찾기 결과 2 창**</span><span class="sxs-lookup"><span data-stu-id="55b63-173">**Find Results 2 window**</span></span>  
 <span data-ttu-id="55b63-174">이 확인란을 선택하면 현재 검색 결과가 찾기 결과 2 창의 내용에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-174">When this check box is selected, the results of the current search will be appended to the content of the Find Results 2 window.</span></span> <span data-ttu-id="55b63-175">이 창은 자동으로 열려 검색 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-175">This window opens automatically to display your search results.</span></span> <span data-ttu-id="55b63-176">이 창을 수동으로 열려면 **보기** 메뉴의 **다른 창** 을 클릭한 다음 **찾기 결과 2**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-176">To open this window manually, click **Other Windows** on the **View** menu and then click **Find Results 2**.</span></span>  
  
 <span data-ttu-id="55b63-177">**파일 이름만 표시**</span><span class="sxs-lookup"><span data-stu-id="55b63-177">**Display file names only**</span></span>  
 <span data-ttu-id="55b63-178">검색 조건과 일치하는 각 항목 대신 검색 조건과 일치하는 항목이 포함된 파일 단위로 찾기 결과 1 또는 찾기 결과 2 창에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-178">Displays one entry per file containing a search match rather than one entry per search match in either the Find Results 1 or Find Results 2 window.</span></span> <span data-ttu-id="55b63-179">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서는 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-179">This option is not available in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="55b63-180">**모두 바꾸기를 실행한 후 수정한 파일 열어 두기**</span><span class="sxs-lookup"><span data-stu-id="55b63-180">**Keep modified files open after Replace All**</span></span>  
 <span data-ttu-id="55b63-181">이 확인란을 선택하면 변경 내용을 실행 취소하거나 저장할 수 있도록 바꾸기를 수행한 모든 파일을 열어 둡니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-181">When selected, leaves open all files in which replacements have been made, so you can undo or save the changes.</span></span> <span data-ttu-id="55b63-182">메모리 제약 때문에 바꾸기 작업 후에 열어 둘 수 있는 파일 수는 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-182">Memory constraints might limit the number of files that can remain open after a replace operation.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="55b63-183">편집하기 위해 열어 둔 파일에 대해서만 **실행 취소** 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-183">You can use **Undo** only on files that remain open for editing.</span></span> <span data-ttu-id="55b63-184">이 옵션을 선택하지 않으면 편집하기 위해 열어 두지 않은 파일은 계속 닫혀 있으며 해당 파일에 대해 **실행 취소** 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-184">If this option is not selected, files that were not already open for editing will remain closed, and no **Undo** option will be available in those files.</span></span>  
  
## <a name="find-and-replace-views"></a><span data-ttu-id="55b63-185">찾기 및 바꾸기 뷰</span><span class="sxs-lookup"><span data-stu-id="55b63-185">Find and Replace Views</span></span>  
 <span data-ttu-id="55b63-186">찾기 및 바꾸기 창의 위쪽에 있는 탭에는 **뷰** 메뉴가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-186">The tabs at the top of the Find and Replace window include **View** menus.</span></span> <span data-ttu-id="55b63-187">이러한 메뉴를 사용하면 활성 창에서 표시할 필드 집합을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-187">These menus enable you to choose a set of fields to display in the active pane.</span></span> <span data-ttu-id="55b63-188">찾기 및 바꾸기 창은 사용하기 편한 위치에 도킹한 다음 탭 사이 및 뷰 사이를 오가며 찾기 또는 바꾸기 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-188">You can leave the Find and Replace window docked in a convenient location and then change from tab to tab and view to view to perform any type of find or replace operation.</span></span>  
  
 <span data-ttu-id="55b63-189">**빠른 찾기로 전환**</span><span class="sxs-lookup"><span data-stu-id="55b63-189">**Switch to Quick Find**</span></span>  
 <span data-ttu-id="55b63-190">이 도구 모음 탭은 대화 상자를 **빠른 찾기** 대화 상자로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-190">This toolbar tab changes the dialog box to a **Quick Find** dialog box.</span></span>  
  
 <span data-ttu-id="55b63-191">**파일에서 찾기로 전환**</span><span class="sxs-lookup"><span data-stu-id="55b63-191">**Switch to Find in Files**</span></span>  
 <span data-ttu-id="55b63-192">이 도구 모음 탭은 대화 상자를 **파일에서 찾기** 대화 상자로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-192">This toolbar tab changes the dialog box to a **Find in Files** dialog box.</span></span>  
  
 <span data-ttu-id="55b63-193">**기호 찾기로 전환**</span><span class="sxs-lookup"><span data-stu-id="55b63-193">**Switch to Find Symbols**</span></span>  
 <span data-ttu-id="55b63-194">이 도구 모음 탭은 대화 상자를 **기호 찾기** 대화 상자로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="55b63-194">This toolbar tab changes the dialog box to a **Find in Symbols** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55b63-195">참고 항목</span><span class="sxs-lookup"><span data-stu-id="55b63-195">See Also</span></span>  
 [<span data-ttu-id="55b63-196">SQL Server Management Studio 바로 가기 키</span><span class="sxs-lookup"><span data-stu-id="55b63-196">SQL Server Management Studio Keyboard Shortcuts</span></span>](../../ssms/sql-server-management-studio-keyboard-shortcuts.md)  

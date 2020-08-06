---
title: 파일에서 바꾸기
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Replace in Files dialog box
ms.assetid: 51191c0a-e022-41d6-8473-5cb3c6596862
author: rothja
ms.author: jroth
ms.openlocfilehash: ad7f23cfc8ec083d5cf2d7dcadefd3a8c27176e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647592"
---
# <a name="replace-in-files"></a><span data-ttu-id="cd50c-102">파일에서 바꾸기</span><span class="sxs-lookup"><span data-stu-id="cd50c-102">Replace in Files</span></span>
  <span data-ttu-id="cd50c-103">찾기 및 바꾸기 창의 **파일에서 바꾸기** 탭을 사용하여 지정한 파일 집합의 코드에서 문자열이나 식을 검색하고 일치하는 항목을 일부 또는 모두 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-103">The **Replace in Files** tab of the Find and Replace window enables you to search the code of a specified set of files for a string or expression and change some or all of the matches found.</span></span> <span data-ttu-id="cd50c-104">**결과 옵션**에서 선택한 찾기 결과 창에 일치하는 항목과 수행한 동작이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-104">The matches found and actions taken are listed in the Find Results window selected in **Result Options**.</span></span>  
  
 <span data-ttu-id="cd50c-105">도구 모음 단추 및 바로 가기 키를 사용하여 **찾기 및 바꾸기** 대화 상자를 열 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-105">Toolbar buttons and shortcut keys are also available to open the **Find and Replace** dialog box.</span></span>  
  
## <a name="find-what"></a><span data-ttu-id="cd50c-106">찾을 내용</span><span class="sxs-lookup"><span data-stu-id="cd50c-106">Find What</span></span>  
 <span data-ttu-id="cd50c-107">**파일에서 바꾸기** 탭의 컨트롤을 사용하여 검색할 문자열이나 식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-107">These controls on the **Replace in Files** tab enable you to specify the string or expression that will be matched.</span></span>  
  
 <span data-ttu-id="cd50c-108">**찾을 내용**</span><span class="sxs-lookup"><span data-stu-id="cd50c-108">**Find what**</span></span>  
 <span data-ttu-id="cd50c-109">검색할 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-109">Type the text to search for.</span></span> <span data-ttu-id="cd50c-110">대화 상자에서는 대화 상자를 열기 전에 커서로 선택한 텍스트, 가까이 위치한 텍스트 또는 이전에 검색한 텍스트를 사용하여 가능한 검색 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-110">The dialog box attempts to fill in a probable search text, using text selected with the cursor before opening the dialog box, or nearby text, or previously searched-for text.</span></span> <span data-ttu-id="cd50c-111">드롭다운 목록에서 검색 문자열을 선택하여 가장 최근에 사용한 20개의 문자열을 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-111">You can reuse one of the last 20 search strings by selecting it from this drop-down list.</span></span>  
  
 <span data-ttu-id="cd50c-112">**[와일드카드가 포함된 문자열]**</span><span class="sxs-lookup"><span data-stu-id="cd50c-112">**[string with wildcards]**</span></span>  
 <span data-ttu-id="cd50c-113">검색 문자열에 별표(`*`) 및 물음표(`?`)와 같은 와일드카드를 사용하려면 **찾기 옵션** 아래의 **사용** 확인란을 선택한 다음 **와일드카드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-113">If you want to use wildcards such as asterisks (`*`) and question marks (`?`) in your search string, select the **Use** check box under **Find Options** and then click **Wildcards**.</span></span>  
  
 <span data-ttu-id="cd50c-114">**[정규식]**</span><span class="sxs-lookup"><span data-stu-id="cd50c-114">**[regular expression]**</span></span>  
 <span data-ttu-id="cd50c-115">검색 엔진에서 검색 문자열을 정규식으로 해석하려면 **찾기 옵션** 아래의 **사용** 확인란을 선택한 다음 **정규식**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-115">To cause the search engine to interpret your search string as a regular expression, select the **Use** check box under **Find Options** and then click **Regular expressions**.</span></span>  
  
 <span data-ttu-id="cd50c-116">**식 작성기**</span><span class="sxs-lookup"><span data-stu-id="cd50c-116">**Expression Builder**</span></span>  
 <span data-ttu-id="cd50c-117">**찾기 옵션** 에서 **사용** 확인란을 선택하면 **찾을 내용**입력란 옆에 있는 삼각형 단추가 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-117">This triangular button next to the **Find what** box becomes available when the **Use** check box is selected in **Find Options**.</span></span> <span data-ttu-id="cd50c-118">이 단추를 클릭하면 선택한 **사용** 옵션에 따라 와일드카드 또는 정규식 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-118">Click this button to display a list of wildcards or regular expressions, depending upon the **Use** option selected.</span></span> <span data-ttu-id="cd50c-119">이 목록에서 항목을 선택하면 해당 항목이 **찾을 내용** 입력란에 지정된 문자열에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-119">Choosing any item from this list adds it to the string specified in the **Find what** box.</span></span>  
  
## <a name="replace-with"></a><span data-ttu-id="cd50c-120">바꿀 항목</span><span class="sxs-lookup"><span data-stu-id="cd50c-120">Replace With</span></span>  
 <span data-ttu-id="cd50c-121">이러한 컨트롤을 사용하면 일치하는 문자열 또는 식의 자리에 삽입할 내용을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-121">These controls enable you to specify what will be inserted in the place of the matched string or expression.</span></span>  
  
 <span data-ttu-id="cd50c-122">**바꿀 내용**</span><span class="sxs-lookup"><span data-stu-id="cd50c-122">**Replace with**</span></span>  
 <span data-ttu-id="cd50c-123">**찾을 내용** 에 지정된 문자열의 인스턴스를 다른 문자열로 바꾸려면 이 필드에 바꿀 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-123">To replace instances of the string specified in **Find what** with another string, enter the replacement string in this field.</span></span> <span data-ttu-id="cd50c-124">**찾을 내용**에 지정된 문자열의 인스턴스를 삭제하려면 이 입력란을 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-124">To delete instances of the string specified in **Find what**, leave this box blank.</span></span> <span data-ttu-id="cd50c-125">가장 최근에 입력한 20개의 항목을 표시하려면 드롭다운 목록을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-125">Select the drop-down list to display the last 20 items entered.</span></span> <span data-ttu-id="cd50c-126">**바꿀 내용** 입력란에 지정된 문자열에 정규식을 포함하려면 **사용** 확인란을 클릭한 다음 **정규식** 옵션을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-126">To include regular expressions in the string specified in the **Replace with** box, click the **Use** check box and then click the **Regular Expressions** option.</span></span>  
  
 <span data-ttu-id="cd50c-127">**식 작성기**</span><span class="sxs-lookup"><span data-stu-id="cd50c-127">**Expression Builder**</span></span>  
 <span data-ttu-id="cd50c-128">**찾기 옵션** 에서 **사용** 확인란을 선택하면 **바꿀 내용**입력란 옆에 있는 삼각형 단추가 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-128">This triangular button next to the **Replace with** box becomes available when the **Use** check box is selected in **Find Options**.</span></span> <span data-ttu-id="cd50c-129">이 단추를 클릭하면 선택한 **사용** 옵션에 따라 와일드카드 또는 정규식 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-129">Click this button to display a list of wildcards or regular expressions, depending upon the **Use** option selected.</span></span> <span data-ttu-id="cd50c-130">이 목록에서 항목을 클릭하면 해당 항목이 **바꿀 내용** 입력란에 지정된 문자열에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-130">Clicking any item in this list adds it to the string specified in the **Replace with** box.</span></span>  
  
 <span data-ttu-id="cd50c-131">**바꾸기**</span><span class="sxs-lookup"><span data-stu-id="cd50c-131">**Replace**</span></span>  
 <span data-ttu-id="cd50c-132">**찾을 내용** 에 지정된 문자열의 현재 인스턴스를 **바꿀 내용** 입력란에 지정된 문자열로 바꾸고 **찾는 위치**에 지정된 범위 내에서 다음 인스턴스를 찾으려면 이 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-132">Click this button to replace the current instance of the string specified in **Find what** with the string specified in the **Replace with** box, and find the next instance within the scope specified in **Look in**.</span></span>  
  
 <span data-ttu-id="cd50c-133">**모두 바꾸기**</span><span class="sxs-lookup"><span data-stu-id="cd50c-133">**Replace all**</span></span>  
 <span data-ttu-id="cd50c-134">**찾는 위치** 에 지정된 범위 내의 모든 파일에서 **찾을 내용** 에 지정된 문자열을 **바꿀 내용**확인란에 지정된 문자열로 바꾸려면 이 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-134">Click this button to replace all instances of the string specified in **Find what** with the string specified in the **Replace with** box, in all files within the scope specified in **Look in**.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="cd50c-135">**찾는 위치** 에 수정하려는 파일만 포함되도록 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-135">Make sure that **Look in** is set to include only those files that you want to modify.</span></span>  
  
 <span data-ttu-id="cd50c-136">**모두 바꾸기를 실행한 후 수정한 파일 열어 두기** 옵션이 포함된 미리 알림이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-136">A reminder is displayed that includes a **Keep modified files open** option.</span></span> <span data-ttu-id="cd50c-137">**실행 취소** 옵션을 유지하려면 이 옵션을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-137">To retain the **Undo** option, you must select this option.</span></span> <span data-ttu-id="cd50c-138">**실행 취소** 는 수정 후에 편집을 위해 계속 열려 있는 파일에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-138">**Undo** is only available in files that remain open for editing after they are modified.</span></span>  
  
 <span data-ttu-id="cd50c-139">**파일 건너뛰기**</span><span class="sxs-lookup"><span data-stu-id="cd50c-139">**Skip File**</span></span>  
 <span data-ttu-id="cd50c-140">**찾는 위치** 에 여러 파일이 포함될 때 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-140">Becomes available when **Look in** includes multiple files.</span></span> <span data-ttu-id="cd50c-141">현재 파일을 검색 또는 수정하지 않으려면 이 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-141">Click this button if you do not want to search or modify the current file.</span></span> <span data-ttu-id="cd50c-142">검색은 **찾는 위치**의 목록에 있는 다음 파일에서 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-142">The search will continue in the next file on the list in **Look in**.</span></span>  
  
## <a name="look-in"></a><span data-ttu-id="cd50c-143">찾는 위치</span><span class="sxs-lookup"><span data-stu-id="cd50c-143">Look In</span></span>  
 <span data-ttu-id="cd50c-144">**찾는 위치** 드롭다운 목록에서 선택한 옵션에 따라 **파일에서 바꾸기** 를 사용할 때 현재 활성 파일에서만 검색할지 특정 폴더 내에 저장된 파일을 모두 검색할지 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-144">The option chosen from the **Look in** drop-down list determines whether **Replace in Files** searches only in currently active files or searches all files stored within certain folders.</span></span> <span data-ttu-id="cd50c-145">목록에서 검색 범위를 선택 하거나 폴더 경로를 입력 하거나 **찾아보기** 단추를 클릭 하 여 **사용자 지정 디렉터리 집합** 대화 상자를 표시 하 고 검색할 폴더 집합을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-145">Select a search scope from the list, type a folder path, or click the **Browse** button to display the **Custom Directory Set** dialog box and choose a set of folders to search.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cd50c-146">**찾는 위치** 옵션을 선택하면 원본 코드 제어에서 체크 아웃한 파일을 검색합니다. 즉, 로컬 컴퓨터로 다운로드한 버전만 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-146">If the **Look in** option selected causes you to search a file that you have checked out from source code control, only the version of that file which has been downloaded to your local computer is searched.</span></span>  
  
 <span data-ttu-id="cd50c-147">**찾는 위치**</span><span class="sxs-lookup"><span data-stu-id="cd50c-147">**Look in**</span></span>  
 <span data-ttu-id="cd50c-148">이 목록에서 미리 정의된 검색 범위를 선택하거나 **사용자 지정 디렉터리 집합** 대화 상자를 사용하여 원하는 디렉터리 집합을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-148">Select a predefined search scope from this list, or use the **Custom Directory Set** dialog box to enter your own set of directories.</span></span>  
  
 <span data-ttu-id="cd50c-149">**현재 문서**</span><span class="sxs-lookup"><span data-stu-id="cd50c-149">**Current Document**</span></span>  
 <span data-ttu-id="cd50c-150">이 옵션은 편집기에 문서가 열려 있을 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-150">This option is available when a document is open in an editor.</span></span> <span data-ttu-id="cd50c-151">**찾을 내용**에 지정된 문자열을 활성 문서에서만 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-151">Searches only the active document for the string specified in **Find what**.</span></span>  
  
 <span data-ttu-id="cd50c-152">**모든 열린 문서**</span><span class="sxs-lookup"><span data-stu-id="cd50c-152">**All Open Documents**</span></span>  
 <span data-ttu-id="cd50c-153">편집하기 위해 현재 열려 있는 모든 파일을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-153">Searches all files currently opened for editing.</span></span>  
  
 <span data-ttu-id="cd50c-154">**현재 프로젝트**</span><span class="sxs-lookup"><span data-stu-id="cd50c-154">**Current Project**</span></span>  
 <span data-ttu-id="cd50c-155">활성 프로젝트에 있는 모든 파일을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-155">Searches all files in the active project.</span></span>  
  
 <span data-ttu-id="cd50c-156">**전체 솔루션**</span><span class="sxs-lookup"><span data-stu-id="cd50c-156">**Entire Solution**</span></span>  
 <span data-ttu-id="cd50c-157">활성 솔루션에 있는 모든 파일을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-157">Searches all files in the active solution.</span></span>  
  
 <span data-ttu-id="cd50c-158">**하위 폴더 포함**</span><span class="sxs-lookup"><span data-stu-id="cd50c-158">**Include subfolders**</span></span>  
 <span data-ttu-id="cd50c-159">**찾는 위치** 에서 지정한 폴더의 하위 폴더도 검색하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-159">Specifies that subfolders of the folder specified in **Look in** will be searched.</span></span> <span data-ttu-id="cd50c-160">이 옵션을 사용하려면 사용자 지정 디렉터리 집합이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-160">It requires a custom directory set.</span></span>  
  
 <span data-ttu-id="cd50c-161">**찾아보기(...)**</span><span class="sxs-lookup"><span data-stu-id="cd50c-161">**Browse (...)**</span></span>  
 <span data-ttu-id="cd50c-162">**찾는 위치** 상자에 입력할 명명된 디렉터리 집합을 조합, 편집, 저장 및 선택할 수 있는 **검색 폴더 선택** 대화 상자를 표시하려면 이 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-162">Click this button to display the **Choose Search Folders** dialog box, where you can assemble, edit, save, and select named sets of directories to enter in the **Look in** box.</span></span>  
  
## <a name="find-options"></a><span data-ttu-id="cd50c-163">사용</span><span class="sxs-lookup"><span data-stu-id="cd50c-163">Find Options</span></span>  
 <span data-ttu-id="cd50c-164">**찾기 옵션** 섹션을 확장하거나 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-164">You can expand or collapse the **Find Options** section.</span></span> <span data-ttu-id="cd50c-165">다음과 같은 옵션을 선택하거나 선택 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-165">The following options can be selected or cleared.</span></span>  
  
 <span data-ttu-id="cd50c-166">**대/소문자 구분**</span><span class="sxs-lookup"><span data-stu-id="cd50c-166">**Match case**</span></span>  
 <span data-ttu-id="cd50c-167">이 확인란을 선택하면 찾기 결과 창에 **찾을 내용** 에 지정된 문자열의 인스턴스 중 내용과 대/소문자가 모두 일치하는 인스턴스만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-167">When this check box is selected, the Find Results windows will only display instances of the string specified in **Find what** that are matched both by content and by case.</span></span> <span data-ttu-id="cd50c-168">예를 들어 대 **/소문자 구분** 확인란을 선택 하 고 **myobject** 를 검색 하면 "myobject"는 반환 되지만 "MYOBJECT" 또는 "myobject"는 반환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-168">For example, a search for **MyObject** with the **Match case** check box selected will return "MyObject" but not "myobject" or "MYOBJECT".</span></span>  
  
 <span data-ttu-id="cd50c-169">**단어 단위로**</span><span class="sxs-lookup"><span data-stu-id="cd50c-169">**Match whole word**</span></span>  
 <span data-ttu-id="cd50c-170">이 확인란을 선택하면 **찾을 내용** 에 지정한 문자열과 단어 단위로 일치하는 인스턴스만 찾기 결과 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-170">When this check box is selected, the Find Results windows will only display instances of the string specified in **Find what** that are matched in complete words.</span></span> <span data-ttu-id="cd50c-171">예를 들어 **MyObject** 를 검색하면 "MyObject"는 반환되지만 "CMyObject"나 "MyObjectC"는 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-171">For example, a search for **MyObject** will return "MyObject" but not "CMyObject" or "MyObjectC."</span></span>  
  
 <span data-ttu-id="cd50c-172">**사용**</span><span class="sxs-lookup"><span data-stu-id="cd50c-172">**Use**</span></span>  
 <span data-ttu-id="cd50c-173">**찾을 내용** 또는 **바꿀 내용** 입력란에 입력한 특수 문자의 해석 방법을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-173">Indicates how to interpret special characters entered in the **Find what** or **Replace with** text boxes.</span></span> <span data-ttu-id="cd50c-174">옵션에는 **와일드카드** 및 **정규식**이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-174">The options include **Wildcards** and **Regular Expressions**.</span></span>  
  
 <span data-ttu-id="cd50c-175">**정규식**</span><span class="sxs-lookup"><span data-stu-id="cd50c-175">**Regular Expressions**</span></span>  
 <span data-ttu-id="cd50c-176">특수 표기를 사용하여 일치하는 텍스트의 패턴을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-176">Special notations define patterns of text to match.</span></span> <span data-ttu-id="cd50c-177">목록을 보려면 [정규식으로 텍스트 검색](search-text-with-regular-expressions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd50c-177">For a list, see [Search Text with Regular Expressions](search-text-with-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="cd50c-178">**와일드카드**</span><span class="sxs-lookup"><span data-stu-id="cd50c-178">**Wildcards**</span></span>  
 <span data-ttu-id="cd50c-179">별표(`*`) 및 물음표(`?`)와 같은 특수 문자는 하나 이상의 문자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-179">Special characters such as asterisks (`*`) and question marks (`?`) represent one or more characters.</span></span> <span data-ttu-id="cd50c-180">목록을 보려면 [와일드카드로 텍스트 검색](search-text-with-wildcards.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd50c-180">For a list, see [Search Text with Wildcards](search-text-with-wildcards.md).</span></span>  
  
 <span data-ttu-id="cd50c-181">**이 파일 형식 보기**</span><span class="sxs-lookup"><span data-stu-id="cd50c-181">**Look at these file types**</span></span>  
 <span data-ttu-id="cd50c-182">이 목록은 **찾는 위치**에 지정한 디렉터리에서 검색할 파일 유형을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-182">This list indicates the types of files to search through in the directories specified in **Look in**.</span></span> <span data-ttu-id="cd50c-183">이 상자를 비워 두면 **찾는 위치** 에 지정된 디렉터리의 모든 파일이 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-183">If this box is left blank, all of the files in the directories specified in **Look in** will be searched.</span></span>  
  
```  
*.[ext]; *.[ext] (manual)  
```  
  
 <span data-ttu-id="cd50c-184">특정 유형의 파일을 찾으려면 파일 이름에 별표 와일드카드(`*`)를 입력하고 뒤에 마침표(`.`)와 파일 확장명을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-184">To find files of a particular type, enter an asterisk wildcard (`*`) for the file name, followed by a period (`.`) and the file extension.</span></span> <span data-ttu-id="cd50c-185">둘 이상의 파일 유형을 찾으려면 여러 개의 검색 문자열을 세미콜론(`;`)으로 구분하여 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-185">To find more than one file type, enter multiple search strings separated by a semicolon (`;`).</span></span>  
  
```  
*.[ext]; *.[ext] (from list)  
```  
  
 <span data-ttu-id="cd50c-186">특정 유형의 파일을 찾는 미리 구성된 검색 문자열을 입력하려면 목록에서 임의 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-186">Select any item in the list to enter a preconfigured search string that will find files of particular types.</span></span>  
  
## <a name="result-options"></a><span data-ttu-id="cd50c-187">결과 옵션</span><span class="sxs-lookup"><span data-stu-id="cd50c-187">Result Options</span></span>  
 <span data-ttu-id="cd50c-188">**결과 옵션** 섹션은 확장하거나 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-188">You can expand or collapse the **Result Options** section.</span></span> <span data-ttu-id="cd50c-189">다음과 같은 옵션을 선택하거나 선택 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-189">The following options can be selected or cleared.</span></span>  
  
 <span data-ttu-id="cd50c-190">**찾기 결과 1 창**</span><span class="sxs-lookup"><span data-stu-id="cd50c-190">**Find Results 1 window**</span></span>  
 <span data-ttu-id="cd50c-191">이 확인란을 선택하면 현재 검색 결과가 찾기 결과 1 창의 내용에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-191">When this check box is selected, the results of the current search will be appended to the content of the Find Results 1 window.</span></span> <span data-ttu-id="cd50c-192">이 창은 자동으로 열려 검색 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-192">This window opens automatically to display your search results.</span></span> <span data-ttu-id="cd50c-193">이 창을 수동으로 열려면 **보기** 메뉴의 **다른 창** 을 클릭한 다음 **찾기 결과 1**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-193">To open this window manually, click **Other Windows** on the **View** menu and then click **Find Results 1**.</span></span>  
  
 <span data-ttu-id="cd50c-194">**찾기 결과 2 창**</span><span class="sxs-lookup"><span data-stu-id="cd50c-194">**Find Results 2 window**</span></span>  
 <span data-ttu-id="cd50c-195">이 확인란을 선택하면 현재 검색 결과가 찾기 결과 2 창의 내용에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-195">When this check box is selected selected, the results of the current search will be appended to the content of the Find Results 2 window.</span></span> <span data-ttu-id="cd50c-196">이 창은 자동으로 열려 검색 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-196">This window opens automatically to display your search results.</span></span> <span data-ttu-id="cd50c-197">이 창을 수동으로 열려면 **보기** 메뉴의 **다른 창** 을 클릭한 다음 **찾기 결과 2**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-197">To open this window manually, click **Other Windows** on the **View** menu and then click **Find Results 2**.</span></span>  
  
 <span data-ttu-id="cd50c-198">**파일 이름만 표시**</span><span class="sxs-lookup"><span data-stu-id="cd50c-198">**Display file names only**</span></span>  
 <span data-ttu-id="cd50c-199">검색 조건과 일치하는 각 항목 대신 검색 조건과 일치하는 항목이 포함된 파일 단위로 찾기 결과 1 또는 찾기 결과 2 창에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-199">Displays one entry per file containing a search match rather than one entry per search match in either the Find Results 1 or Find Results 2 window.</span></span> <span data-ttu-id="cd50c-200">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서는 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-200">This option is not available in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="cd50c-201">**모두 바꾸기를 실행한 후 수정한 파일 열어 두기**</span><span class="sxs-lookup"><span data-stu-id="cd50c-201">**Keep modified files open after Replace All**</span></span>  
 <span data-ttu-id="cd50c-202">이 확인란을 선택하면 변경 내용을 실행 취소하거나 저장할 수 있도록 바꾸기를 수행한 모든 파일을 열어 둡니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-202">When selected, leaves open all files in which replacements have been made, so you can undo or save the changes.</span></span> <span data-ttu-id="cd50c-203">메모리 제약 때문에 바꾸기 작업 후에 열어 둘 수 있는 파일 수는 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-203">Memory constraints might limit the number of files that can remain open after a replace operation.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="cd50c-204">편집하기 위해 열어 둔 파일에 대해서만 **실행 취소** 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-204">You can use **Undo** only on files that remain open for editing.</span></span> <span data-ttu-id="cd50c-205">이 옵션을 선택하지 않으면 편집하기 위해 열어 두지 않은 파일은 계속 닫혀 있으며 해당 파일에 대해 **실행 취소** 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-205">If this option is not selected, files that were not already open for editing will remain closed, and no **Undo** option will be available in those files.</span></span>  
  
## <a name="find-and-replace-views"></a><span data-ttu-id="cd50c-206">찾기 및 바꾸기 뷰</span><span class="sxs-lookup"><span data-stu-id="cd50c-206">Find and Replace Views</span></span>  
 <span data-ttu-id="cd50c-207">찾기 및 바꾸기 창의 위쪽에 있는 탭에는 **보기** 메뉴가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-207">The tabs at the top of the Findand Replace window include **View** menus.</span></span> <span data-ttu-id="cd50c-208">이러한 메뉴를 사용하면 활성 창에서 표시할 필드 집합을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-208">These menus enable you to choose a set of fields to display in the active pane.</span></span> <span data-ttu-id="cd50c-209">찾기 및 바꾸기 창은 사용하기 편한 위치에 도킹한 다음 탭 및 보기 사이를 오가며 찾기 또는 바꾸기 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-209">You can leave the Find and Replace window docked in a convenient location, and then change from tab to tab and view to view to perform any type of find or replace operation.</span></span>  
  
 <span data-ttu-id="cd50c-210">**빠른 찾기로 전환**</span><span class="sxs-lookup"><span data-stu-id="cd50c-210">**Switch to Quick Find**</span></span>  
 <span data-ttu-id="cd50c-211">이 도구 모음 탭은 대화 상자를 **빠른 찾기** 대화 상자로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-211">This toolbar tab changes the dialog box to a **Quick Find** dialog box.</span></span>  
  
 <span data-ttu-id="cd50c-212">**파일에서 찾기로 전환**</span><span class="sxs-lookup"><span data-stu-id="cd50c-212">**Switch to Find in Files**</span></span>  
 <span data-ttu-id="cd50c-213">이 도구 모음 탭은 대화 상자를 **파일에서 찾기** 대화 상자로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-213">This toolbar tab changes the dialog box to a **Find in Files** dialog box.</span></span>  
  
 <span data-ttu-id="cd50c-214">**기호 찾기로 전환**</span><span class="sxs-lookup"><span data-stu-id="cd50c-214">**Switch to Find Symbols**</span></span>  
 <span data-ttu-id="cd50c-215">이 도구 모음 탭은 대화 상자를 **기호 찾기** 대화 상자로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="cd50c-215">This toolbar tab changes the dialog box to a **Find in Symbols** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd50c-216">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cd50c-216">See Also</span></span>  
 [<span data-ttu-id="cd50c-217">SQL Server Management Studio 바로 가기 키</span><span class="sxs-lookup"><span data-stu-id="cd50c-217">SQL Server Management Studio Keyboard Shortcuts</span></span>](../../ssms/sql-server-management-studio-keyboard-shortcuts.md)  

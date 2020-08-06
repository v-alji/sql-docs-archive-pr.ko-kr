---
title: 데이터 정렬 대화 상자(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.definecolumncollation
- vdtsql.chm:65561
ms.assetid: e4020f79-7abf-4839-b9b2-984ef7049817
author: stevestein
ms.author: sstein
ms.openlocfilehash: d551b2ae7ca27250c144afedf13038efd78ad6ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661457"
---
# <a name="collation-dialog-box-visual-database-tools"></a><span data-ttu-id="6cbc0-102">데이터 정렬 대화 상자(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="6cbc0-102">Collation Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="6cbc0-103">이 대화 상자를 사용하면 열의 데이터 정렬 순서를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-103">This dialog box lets you specify a collation sequence for the column.</span></span> <span data-ttu-id="6cbc0-104">열의 데이터 정렬 순서는 열의 값을 다른 열이나 상수 값과 비교하는 모든 작업에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-104">A column's collation sequence is used in any operation that compares values of the column to another column or to constant values.</span></span> <span data-ttu-id="6cbc0-105">이 순서는 SUBSTRING 및 CHARINDEX 등과 같은 일부 문자열 함수의 동작에도 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-105">It also affects the behavior of some string functions, such as SUBSTRING and CHARINDEX.</span></span> <span data-ttu-id="6cbc0-106">열의 데이터 정렬 순서 설정이 미치는 영향에 대한 전체 목록은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-106">For a complete list of the effects of a column's collation setting, see the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] documentation.</span></span>  
  
 <span data-ttu-id="6cbc0-107">이 대화 상자는 다음과 같은 경우에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-107">This dialog box appears:</span></span>  
  
-   <span data-ttu-id="6cbc0-108">**열 속성** 탭의 **데이터 정렬** 필드에 잘못된 데이터 정렬 이름을 입력한 경우</span><span class="sxs-lookup"><span data-stu-id="6cbc0-108">If you enter an invalid collation name in the **Collation** field on the **Column Properties** tab.</span></span>  
  
-   <span data-ttu-id="6cbc0-109">**열 속성** 탭의 **데이터 정렬** 필드를 클릭한 다음, 필드의 오른쪽에 있는 줄임표 단추( **...** )를 클릭한 경우</span><span class="sxs-lookup"><span data-stu-id="6cbc0-109">If you click in the **Collation** field on the **Column Properties** tab, and then click the ellipsis button (**...**) to the right of the field.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6cbc0-110">옵션</span><span class="sxs-lookup"><span data-stu-id="6cbc0-110">Options</span></span>  
 <span data-ttu-id="6cbc0-111">**SQL 데이터 정렬**</span><span class="sxs-lookup"><span data-stu-id="6cbc0-111">**SQL Collation**</span></span>  
 <span data-ttu-id="6cbc0-112">드롭다운 목록의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 정의되어 있는 데이터 정렬 순서 중에서 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-112">Choose among the collation sequences defined by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the drop-down list.</span></span>  
  
 <span data-ttu-id="6cbc0-113">**Windows 데이터 정렬**</span><span class="sxs-lookup"><span data-stu-id="6cbc0-113">**Windows Collation**</span></span>  
 <span data-ttu-id="6cbc0-114">드롭다운 목록의 Windows에 정의되어 있는 데이터 정렬 순서 중에서 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-114">Choose among the collation sequences defined by Windows from the drop-down list.</span></span>  
  
 <span data-ttu-id="6cbc0-115">**이진 정렬**</span><span class="sxs-lookup"><span data-stu-id="6cbc0-115">**Binary Sort**</span></span>  
 <span data-ttu-id="6cbc0-116">문자 값의 이진 코드를 사용하여 비교하려는 경우에 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-116">Use the binary codes of character values for comparisons.</span></span> <span data-ttu-id="6cbc0-117">이 옵션을 선택하면 특정 영문자 비교 옵션을 사용할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-117">If you select this option, certain alphabetic comparison options become unavailable.</span></span> <span data-ttu-id="6cbc0-118">예를 들어, 대문자와 소문자는 이진 인코딩이 서로 다르므로 대/소문자를 구분하지 않고 비교하는 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-118">For example, case-insensitive comparisons become unavailable because uppercase letters and lowercase letters have different binary encodings.</span></span> <span data-ttu-id="6cbc0-119">**Windows 데이터 정렬**을 선택한 경우에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-119">Applies only if you select **Windows collation**.</span></span>  
  
 <span data-ttu-id="6cbc0-120">**사전 정렬**</span><span class="sxs-lookup"><span data-stu-id="6cbc0-120">**Dictionary Sort**</span></span>  
 <span data-ttu-id="6cbc0-121">영문자 비교 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-121">Use alphabetic comparison options.</span></span> <span data-ttu-id="6cbc0-122">**Windows 데이터 정렬**을 선택한 경우에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-122">Applies only if you select **Windows collation**.</span></span> <span data-ttu-id="6cbc0-123">영문자 비교 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-123">The alphabetic comparisons options are:</span></span>  
  
-   <span data-ttu-id="6cbc0-124">**대/소문자 구분** 대문자와 소문자를 동일하지 않은 것으로 간주하여 비교하려는 경우에 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-124">**Case Sensitive** Select this if you want comparisons to consider uppercase and lowercase letters to be unequal.</span></span>  
  
-   <span data-ttu-id="6cbc0-125">**악센트 구분** 악센트 부호가 있는 문자와 없는 문자를 동일하지 않은 것으로 간주하여 비교하려는 경우에 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-125">**Accent Sensitive** Select this if you want comparisons to consider accented and unaccented letters to be unequal.</span></span> <span data-ttu-id="6cbc0-126">이 옵션을 선택하면 악센트 부호가 서로 다른 방식으로 추가된 문자도 동일하지 않은 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-126">If you select this, comparisons will also consider differently accented letters to be unequal.</span></span>  
  
-   <span data-ttu-id="6cbc0-127">**일본어 가나 구분** 일본어 가타카나 음절과 히라가나 음절이 동일하지 않은 것으로 간주하여 비교하려는 경우에 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-127">**Kana Sensitive** Select this if you want comparisons to consider katakana and hiragana Japanese syllables to be unequal.</span></span>  
  
-   <span data-ttu-id="6cbc0-128">**전자/반자 구분** 반자 및 전자 문자가 동일하지 않은 것으로 간주하여 비교하려는 경우에 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-128">**Width Sensitive** Select this if you want comparisons to consider half-width and full-width characters to be unequal.</span></span>  
  
 <span data-ttu-id="6cbc0-129">**기본값 복원 단추**</span><span class="sxs-lookup"><span data-stu-id="6cbc0-129">**Restore Default Button**</span></span>  
 <span data-ttu-id="6cbc0-130">데이터베이스의 기본 데이터 정렬 순서를 열에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-130">Apply the default collation sequence for the database to the column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cbc0-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6cbc0-131">See Also</span></span>  
 [<span data-ttu-id="6cbc0-132">집계 쿼리에서 열 작업&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="6cbc0-132">Work with Columns in Aggregate Queries &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  

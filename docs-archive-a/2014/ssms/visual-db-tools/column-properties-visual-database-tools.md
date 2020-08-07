---
title: 열 속성(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.designers.properties.Column.ColumnIdentitySpec
- vdt.designers.properties.Column
- vdt.tablecolumn
- vdt.designers.properties.Column.ColumnComputedColumnSpec
- vdt.designers.properties.Column.ColumnFulltextSpec
ms.assetid: e549a2a8-4154-4ec8-b146-614564169b39
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6aeb4d01cae7c09c27cafa8284638bf0a7de9691
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727811"
---
# <a name="column-properties-visual-database-tools"></a><span data-ttu-id="b635c-102">열 속성(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="b635c-102">Column Properties (Visual Database Tools)</span></span>
  <span data-ttu-id="b635c-103">열 속성 집합에는 테이블 디자이너([!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에서만 사용 가능) 내 **열 속성** 탭에서 볼 수 있는 전체 집합과 서버 탐색기를 사용하여 속성 창에서 볼 수 있는 하위 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-103">There are two sets of properties for columns: a full set that you can see in the **Column Properties** tab within Table Designer (available only for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases) and a subset you can see in the Properties window using Server Explorer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b635c-104">이 항목의 속성은 사전순 대신 범주별로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-104">The properties in this topic are ordered by category rather than alphabet.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b635c-105">활성 설정 또는 버전에 따라 표시되는 대화 상자 및 메뉴 명령이 도움말에 설명된 것과 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b635c-106">설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span>  
  
## <a name="properties-window"></a><span data-ttu-id="b635c-107">속성 창</span><span class="sxs-lookup"><span data-stu-id="b635c-107">Properties Window</span></span>  
 <span data-ttu-id="b635c-108">서버 탐색기에서 열을 선택하면 이러한 속성이 속성 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-108">These properties appear in the Properties window when you select a column in Server Explorer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b635c-109">서버 탐색기를 사용하여 액세스할 수 있는 이러한 속성은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-109">These properties, accessed using Server Explorer, are read-only.</span></span> <span data-ttu-id="b635c-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스의 열 속성을 편집하려면 테이블 디자이너에서 해당 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-110">To edit column properties for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases, select the column in Table Designer.</span></span> <span data-ttu-id="b635c-111">이러한 속성은 이 항목의 뒷부분에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-111">Those properties are described later in this topic.</span></span>  
  
 <span data-ttu-id="b635c-112">**ID 범주**</span><span class="sxs-lookup"><span data-stu-id="b635c-112">**Identity Category**</span></span>  
 <span data-ttu-id="b635c-113">확장하면 **이름** 및 **데이터베이스** 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-113">Expands to show the **Name** and **Database** properties.</span></span>  
  
 <span data-ttu-id="b635c-114">**이름**</span><span class="sxs-lookup"><span data-stu-id="b635c-114">**Name**</span></span>  
 <span data-ttu-id="b635c-115">열의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-115">Shows the name of the column.</span></span>  
  
 <span data-ttu-id="b635c-116">**Database**</span><span class="sxs-lookup"><span data-stu-id="b635c-116">**Database**</span></span>  
 <span data-ttu-id="b635c-117">선택한 열에 대한 데이터 원본의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-117">Shows the name of the data source for the selected column.</span></span> <span data-ttu-id="b635c-118">OLE DB에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-118">(Applies only to OLE DB.)</span></span>  
  
 <span data-ttu-id="b635c-119">**기타 범주**</span><span class="sxs-lookup"><span data-stu-id="b635c-119">**Misc Category**</span></span>  
 <span data-ttu-id="b635c-120">확장하면 나머지 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-120">Expands to show the remaining properties.</span></span>  
  
 <span data-ttu-id="b635c-121">**데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="b635c-121">**Data Type**</span></span>  
 <span data-ttu-id="b635c-122">선택한 열의 데이터 형식을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-122">Shows the data type of the selected column.</span></span> <span data-ttu-id="b635c-123">자세한 내용은 [데이터 형식&#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b635c-123">For more information, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
 <span data-ttu-id="b635c-124">**ID 증가값**</span><span class="sxs-lookup"><span data-stu-id="b635c-124">**Identity Increment**</span></span>  
 <span data-ttu-id="b635c-125">ID 열의 각 후속 행에 대한 **ID 초기값** 에 추가할 증가값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-125">Shows the increment that will be added to the **Identity Seed** for each subsequent row of the identity column.</span></span> <span data-ttu-id="b635c-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-126">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)</span></span>  
  
 <span data-ttu-id="b635c-127">**ID 초기값**</span><span class="sxs-lookup"><span data-stu-id="b635c-127">**Identity Seed**</span></span>  
 <span data-ttu-id="b635c-128">ID 열에 대한 테이블의 첫 번째 행에 할당된 초기값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-128">Shows the seed value assigned to the first row in the table for the identity column.</span></span> <span data-ttu-id="b635c-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-129">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)</span></span>  
  
 <span data-ttu-id="b635c-130">**ID**</span><span class="sxs-lookup"><span data-stu-id="b635c-130">**Is Identity**</span></span>  
 <span data-ttu-id="b635c-131">선택한 열이 테이블에 대한 ID 열인지 여부를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-131">Shows whether the selected column is the identity column for the table.</span></span> <span data-ttu-id="b635c-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-132">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)</span></span>  
  
 <span data-ttu-id="b635c-133">**길이**</span><span class="sxs-lookup"><span data-stu-id="b635c-133">**Length**</span></span>  
 <span data-ttu-id="b635c-134">문자 기반 데이터 형식에 허용되는 문자 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-134">Shows the number of characters allowed for character-based data types.</span></span>  
  
 <span data-ttu-id="b635c-135">**Null 허용**</span><span class="sxs-lookup"><span data-stu-id="b635c-135">**Nullable**</span></span>  
 <span data-ttu-id="b635c-136">열에 Null 값이 허용되는지 여부를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-136">Shows whether or not the column allows null values.</span></span>  
  
 <span data-ttu-id="b635c-137">**정밀도**</span><span class="sxs-lookup"><span data-stu-id="b635c-137">**Precision**</span></span>  
 <span data-ttu-id="b635c-138">숫자 데이터 형식에 허용되는 최대 자릿수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-138">Shows the maximum number of digits allowed for numeric data types.</span></span> <span data-ttu-id="b635c-139">이 속성은 숫자가 아닌 데이터 형식에 대해 **0** 을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-139">This property shows **0** for nonnumeric data types.</span></span>  
  
 <span data-ttu-id="b635c-140">**규모**</span><span class="sxs-lookup"><span data-stu-id="b635c-140">**Scale**</span></span>  
 <span data-ttu-id="b635c-141">숫자 데이터 형식에 대해 소수점 오른쪽에 나타날 수 있는 최대 자릿수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-141">Shows the maximum number of digits that can appear to the right of the decimal point for numeric data types.</span></span> <span data-ttu-id="b635c-142">이 값은 전체 자릿수보다 작거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-142">This value must be less than or equal to the precision.</span></span> <span data-ttu-id="b635c-143">이 속성은 숫자가 아닌 데이터 형식에 대해 **0** 을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-143">This property shows **0** for nonnumeric data types.</span></span>  
  
## <a name="column-properties-tab"></a><span data-ttu-id="b635c-144">열 속성 탭</span><span class="sxs-lookup"><span data-stu-id="b635c-144">Column Properties Tab</span></span>  
 <span data-ttu-id="b635c-145">이러한 속성에 액세스하려면 서버 탐색기에서 열이 속하는 테이블을 마우스 오른쪽 단추로 클릭한 다음 **테이블 정의 열기**를 선택하고 테이블 디자이너에서 테이블 표의 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-145">To access these properties, in Server Explorer right-click the table to which the column belongs, choose **Open Table Definition**, and select the row in the table grid in Table Designer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b635c-146">이러한 속성은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-146">These properties apply only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b635c-147">**일반 범주**</span><span class="sxs-lookup"><span data-stu-id="b635c-147">**General Category**</span></span>  
 <span data-ttu-id="b635c-148">확장하면 **이름**, **Null 허용**, **데이터 형식**, **기본값 또는 바인딩**, **길이**, **정밀도**및 **소수 자릿수**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-148">Expands to show **Name**, **Allow Nulls**, **Data Type**, **Default Value or Binding**, **Length**, **Precision**, and **Scale**.</span></span>  
  
 <span data-ttu-id="b635c-149">**이름**</span><span class="sxs-lookup"><span data-stu-id="b635c-149">**Name**</span></span>  
 <span data-ttu-id="b635c-150">열의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-150">Displays the name of the column.</span></span> <span data-ttu-id="b635c-151">이름을 편집하려면 입력란에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-151">To edit the name, type in the text box.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="b635c-152">기존 쿼리, 뷰, 사용자 정의 함수, 저장 프로시저 또는 프로그램에서 해당 열을 참조하는 경우 이름을 수정하면 이러한 개체를 사용할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-152">If existing queries, views, user-defined functions, stored procedures, or programs refer to the column, the name modification will make these objects invalid.</span></span>  
  
 <span data-ttu-id="b635c-153">**Null 허용**</span><span class="sxs-lookup"><span data-stu-id="b635c-153">**Allow Nulls**</span></span>  
 <span data-ttu-id="b635c-154">열의 데이터 형식에 Null 값이 허용되는지 여부를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-154">Shows whether or not the column's data type allows null values.</span></span>  
  
 <span data-ttu-id="b635c-155">**데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="b635c-155">**Data Type**</span></span>  
 <span data-ttu-id="b635c-156">선택한 열의 데이터 형식을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-156">Shows the data type for the selected column.</span></span> <span data-ttu-id="b635c-157">이 속성을 편집하려면 해당 값을 클릭하고 드롭다운 목록을 확장한 다음 다른 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-157">To edit this property, click its value, expand the drop-down list, and choose another value.</span></span> <span data-ttu-id="b635c-158">자세한 내용은 [데이터 형식&#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b635c-158">For more information, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
 <span data-ttu-id="b635c-159">**기본값 또는 바인딩**</span><span class="sxs-lookup"><span data-stu-id="b635c-159">**Default Value or Binding**</span></span>  
 <span data-ttu-id="b635c-160">이 열에 대해 지정한 값이 없는 경우 이 열에 대한 기본값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-160">Shows the default for this column when no value is specified for this column.</span></span> <span data-ttu-id="b635c-161">드롭다운 목록에는 데이터 원본에 정의된 모든 전역 기본값이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-161">The drop-down list contains all global defaults defined in the data source.</span></span> <span data-ttu-id="b635c-162">열을 전역 기본값에 바인딩하려면 드롭다운 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-162">To bind the column to a global default, select from the drop-down list.</span></span> <span data-ttu-id="b635c-163">열에 대한 기본 제약 조건을 만들려면 직접 기본값을 텍스트로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-163">Alternatively, to create a default constraint for the column, type the default value directly as text.</span></span>  
  
 <span data-ttu-id="b635c-164">**길이**</span><span class="sxs-lookup"><span data-stu-id="b635c-164">**Length**</span></span>  
 <span data-ttu-id="b635c-165">문자 기반 데이터 형식에 허용되는 문자 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-165">Shows the number of characters allowed for character-based data types.</span></span> <span data-ttu-id="b635c-166">이 속성은 문자 기반 데이터 형식에 대해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-166">This property is only available for character-based data types.</span></span>  
  
 <span data-ttu-id="b635c-167">**정밀도**</span><span class="sxs-lookup"><span data-stu-id="b635c-167">**Precision**</span></span>  
 <span data-ttu-id="b635c-168">숫자 데이터 형식에 허용되는 최대 자릿수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-168">Shows the maximum number of digits allowed for numeric data types.</span></span> <span data-ttu-id="b635c-169">이 속성은 숫자가 아닌 데이터 형식에 대해 **0** 을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-169">This property shows **0** for nonnumeric data types.</span></span> <span data-ttu-id="b635c-170">이 속성은 숫자 데이터 형식에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-170">This property is only available for numeric data types.</span></span>  
  
 <span data-ttu-id="b635c-171">**규모**</span><span class="sxs-lookup"><span data-stu-id="b635c-171">**Scale**</span></span>  
 <span data-ttu-id="b635c-172">숫자 데이터 형식에 대해 소수점 오른쪽에 나타날 수 있는 최대 자릿수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-172">Shows the maximum number of digits that can appear to the right of the decimal point for numeric data types.</span></span> <span data-ttu-id="b635c-173">이 값은 전체 자릿수보다 작거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-173">This value must be less than or equal to the precision.</span></span> <span data-ttu-id="b635c-174">이 속성은 숫자가 아닌 데이터 형식에 대해 **0** 을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-174">This property shows **0** for nonnumeric data types.</span></span> <span data-ttu-id="b635c-175">이 속성은 숫자 데이터 형식에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-175">This property is only available for numeric data types.</span></span>  
  
 <span data-ttu-id="b635c-176">**테이블 디자이너 범주**</span><span class="sxs-lookup"><span data-stu-id="b635c-176">**Table Designer Category**</span></span>  
 <span data-ttu-id="b635c-177">확장하면 나머지 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-177">Expands to show the remaining properties.</span></span>  
  
 <span data-ttu-id="b635c-178">**데이터 정렬**</span><span class="sxs-lookup"><span data-stu-id="b635c-178">**Collation**</span></span>  
 <span data-ttu-id="b635c-179">선택한 열에 대한 데이터 정렬 설정을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-179">Shows the collation setting for the selected column.</span></span> <span data-ttu-id="b635c-180">이 설정을 변경하려면 **데이터 정렬** 을 클릭한 다음, 값의 오른쪽에 있는 줄임표 **(...)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-180">To change this setting, click **Collation** and then click the ellipses **(...)** to the right of the value.</span></span>  
  
 <span data-ttu-id="b635c-181">**계산 열 사양 범주**</span><span class="sxs-lookup"><span data-stu-id="b635c-181">**Computed Column Specification Category**</span></span>  
 <span data-ttu-id="b635c-182">확장하면 **수식** 및 **지속됨**의 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-182">Expands to show properties for **Formula** and **Is Persisted**.</span></span> <span data-ttu-id="b635c-183">계산 열인 경우 수식도 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-183">If the column is computed, the formula will also be displayed.</span></span> <span data-ttu-id="b635c-184">수식을 편집하려면 이 범주를 확장한 다음 **수식** 속성에서 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-184">To edit the formula, expand this category and edit it in the **Formula** property.</span></span>  
  
 <span data-ttu-id="b635c-185">**수식**</span><span class="sxs-lookup"><span data-stu-id="b635c-185">**Formula**</span></span>  
 <span data-ttu-id="b635c-186">선택한 계산 열에서 사용하는 수식을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-186">Shows the formula that the selected column uses if it is a computed column.</span></span> <span data-ttu-id="b635c-187">이 필드에서 수식을 입력 또는 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-187">In this field you can enter or change a formula.</span></span>  
  
 <span data-ttu-id="b635c-188">**지속됨**</span><span class="sxs-lookup"><span data-stu-id="b635c-188">**Is Persisted**</span></span>  
 <span data-ttu-id="b635c-189">계산 열을 데이터 원본과 함께 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-189">Allows you to save the computed column with the data source.</span></span> <span data-ttu-id="b635c-190">지속형 계산 열은 인덱싱할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-190">A persisted computed column can be indexed.</span></span>  
  
 <span data-ttu-id="b635c-191">**압축 데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="b635c-191">**Condensed Data Type**</span></span>  
 <span data-ttu-id="b635c-192">필드의 데이터 형식에 대한 정보를 SQL CREATE TABLE 문과 동일한 형식으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-192">Displays information about the field's data type, in the same format as the SQL CREATE TABLE statement.</span></span> <span data-ttu-id="b635c-193">예를 들어 최대 길이가 20자인 가변 길이 문자열을 포함하는 필드는 "varchar(20)"으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-193">For example, a field containing a variable-length string with a maximum length of 20 characters would be represented as "varchar(20)."</span></span> <span data-ttu-id="b635c-194">이 속성을 변경하려면 직접 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-194">To change this property, type the value directly.</span></span>  
  
 <span data-ttu-id="b635c-195">**설명**</span><span class="sxs-lookup"><span data-stu-id="b635c-195">**Description**</span></span>  
 <span data-ttu-id="b635c-196">열에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-196">Shows the description of the column.</span></span> <span data-ttu-id="b635c-197">전체 설명을 보거나 편집하려면 설명을 클릭한 다음, 속성의 오른쪽에 있는 줄임표 **(...)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-197">To see the full description or to edit it, click Description, and then click the ellipses **(...)** to the right of the property.</span></span>  
  
 <span data-ttu-id="b635c-198">**전체 텍스트 사양 범주**</span><span class="sxs-lookup"><span data-stu-id="b635c-198">**Full-text Specification Category**</span></span>  
 <span data-ttu-id="b635c-199">확장하면 전체 텍스트 열의 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-199">Expands to show properties specific to full-text columns.</span></span>  
  
 <span data-ttu-id="b635c-200">**전체 텍스트가 인덱싱됨**</span><span class="sxs-lookup"><span data-stu-id="b635c-200">**Is Full-text Indexed**</span></span>  
 <span data-ttu-id="b635c-201">이 열이 전체 텍스트 인덱싱되었는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-201">Indicates whether this column is full-text indexed.</span></span> <span data-ttu-id="b635c-202">이 열의 데이터 형식이 전체 텍스트로 검색 가능한 경우 및 이 열이 속하는 테이블에 전체 텍스트 인덱스가 지정되어 있는 경우에만 이 속성을 **예** 로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-202">This property can be set to **Yes** only if the data type for this column is full-text searchable and if the table to which this column belongs has a full-text index specified for it.</span></span> <span data-ttu-id="b635c-203">이 값을 변경하려면 해당 값을 클릭하고 드롭다운 목록을 확장한 다음 새 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-203">To change this value, click it, expand the drop-down list, and choose a new value.</span></span>  
  
 <span data-ttu-id="b635c-204">**전체 텍스트 형식 열**</span><span class="sxs-lookup"><span data-stu-id="b635c-204">**Full-text type column**</span></span>  
 <span data-ttu-id="b635c-205">IMAGE 유형 열의 문서 유형을 정의하는 데 사용되는 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-205">Shows which column is used to define the document type of a column of type image.</span></span> <span data-ttu-id="b635c-206">IMAGE 데이터 형식을 사용하여 .doc 파일에서 .xml 파일에 이르는 문서를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-206">The image data type can be used to store documents ranging from .doc files to xml files.</span></span>  
  
 <span data-ttu-id="b635c-207">**언어**</span><span class="sxs-lookup"><span data-stu-id="b635c-207">**Language**</span></span>  
 <span data-ttu-id="b635c-208">열을 인덱싱하는 데 사용되는 언어를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-208">Indicates the language used to index the column.</span></span>  
  
 <span data-ttu-id="b635c-209">**통계 의미 체계**</span><span class="sxs-lookup"><span data-stu-id="b635c-209">**Statistical Semantics**</span></span>  
 <span data-ttu-id="b635c-210">선택한 열에 대해 통계 의미 체계 인덱싱을 사용하도록 설정할지 여부를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-210">Select whether to enable statistical semantic indexing for the selected column.</span></span> <span data-ttu-id="b635c-211">자세한 내용은 [의미 체계 검색&#40;SQL Server&#41;](../../relational-databases/search/semantic-search-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b635c-211">For more information, see [Semantic Search &#40;SQL Server&#41;](../../relational-databases/search/semantic-search-sql-server.md).</span></span>  
  
 <span data-ttu-id="b635c-212">**통계 의미 체계** 를 선택하기 전에 **언어**를 선택했으며 선택한 언어에 연결된 의미 체계 언어 모델이 없으면 **통계 의미 체계** 옵션은 **아니요** 로 설정되며 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-212">If you select a **Language** prior to selecting **Statistical Semantics**, and the selected language does not have an associated Semantic Language Model, then the **Statistical Semantics** option is set to **No** and cannot be modified.</span></span> <span data-ttu-id="b635c-213">**언어** 를 선택하기 전에 **통계 의미 체계** 옵션에 대해 **예**를 선택한 경우 **언어** 열에서 사용할 수 있는 언어는 의미 체계 언어 모델이 지원되는 언어로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-213">If you select **Yes** for the **Statistical Semantics** option prior to selecting a **Language**, then the languages available in the **Language** column will be restricted to those for which there is Semantic Language Model support.</span></span>  
  
 <span data-ttu-id="b635c-214">**SQL Server 이외 구독자가 있음**</span><span class="sxs-lookup"><span data-stu-id="b635c-214">**Has Non-SQL Server Subscriber**</span></span>  
 <span data-ttu-id="b635c-215">열에 Microsoft SQL Server 이외의 구독자가 있는지 여부를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-215">Shows whether the column has a non-Microsoft SQL Server subscriber.</span></span>  
  
 <span data-ttu-id="b635c-216">**ID 사양 범주**</span><span class="sxs-lookup"><span data-stu-id="b635c-216">**Identity Specification Category**</span></span>  
 <span data-ttu-id="b635c-217">확장하면 **ID**, **ID 증가값**및 **ID 초기값**의 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-217">Expands to show properties for **Is Identity**, **Identity Increment**, and **Identity Seed**.</span></span>  
  
 <span data-ttu-id="b635c-218">**ID**</span><span class="sxs-lookup"><span data-stu-id="b635c-218">**Is Identity**</span></span>  
 <span data-ttu-id="b635c-219">선택한 열이 테이블에 대한 ID 열인지 여부를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-219">Shows whether the selected column is the identity column for the table.</span></span> <span data-ttu-id="b635c-220">속성을 변경하려면 테이블 디자이너에서 테이블을 연 다음 **속성** 창에서 속성을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-220">To change the property, open the table in Table Designer and edit the properties in the **Properties** window.</span></span> <span data-ttu-id="b635c-221">이 설정은 *int*와 같은 번호 기반 데이터 형식의 열에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-221">This setting applies only to columns with a number-based data type, such as *int*.</span></span>  
  
 <span data-ttu-id="b635c-222">**ID 증가값**</span><span class="sxs-lookup"><span data-stu-id="b635c-222">**Identity Increment**</span></span>  
 <span data-ttu-id="b635c-223">각 후속 행에 대한 **ID 초기값** 에 추가할 증가값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-223">Shows the increment that will be added to the **Identity Seed** for each subsequent row.</span></span> <span data-ttu-id="b635c-224">이 셀에 값을 입력하지 않으면 기본적으로 값 1이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-224">If you leave this cell blank, the value 1 will be assigned by default.</span></span> <span data-ttu-id="b635c-225">이 속성을 편집하려면 직접 새 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-225">To edit this property, type the new value directly.</span></span>  
  
 <span data-ttu-id="b635c-226">**ID 초기값**</span><span class="sxs-lookup"><span data-stu-id="b635c-226">**Identity Seed**</span></span>  
 <span data-ttu-id="b635c-227">테이블의 첫 번째 행에 할당된 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-227">Shows the value assigned to the first row in the table.</span></span> <span data-ttu-id="b635c-228">이 셀에 값을 입력하지 않으면 기본적으로 값 1이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-228">If you leave this cell blank, the value 1 will be assigned by default.</span></span> <span data-ttu-id="b635c-229">이 속성을 편집하려면 직접 새 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-229">To edit this property, type the new value directly.</span></span>  
  
 <span data-ttu-id="b635c-230">**명확함**</span><span class="sxs-lookup"><span data-stu-id="b635c-230">**Is Deterministic**</span></span>  
 <span data-ttu-id="b635c-231">선택한 열의 데이터 형식을 확실하게 결정할 수 있는지 여부를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-231">Shows whether the data type of the selected column can be determined with certainty.</span></span>  
  
 <span data-ttu-id="b635c-232">**DTS 게시됨**</span><span class="sxs-lookup"><span data-stu-id="b635c-232">**Is DTS-published**</span></span>  
 <span data-ttu-id="b635c-233">열의 DTS 게시 여부를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-233">Shows whether the column is DTS-published.</span></span>  
  
 <span data-ttu-id="b635c-234">**인덱싱 가능**</span><span class="sxs-lookup"><span data-stu-id="b635c-234">**Is Indexable**</span></span>  
 <span data-ttu-id="b635c-235">선택한 열을 인덱싱할 수 있는지 여부를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-235">Shows whether the selected column can be indexed.</span></span> <span data-ttu-id="b635c-236">예를 들어 비결정적 계산 열은 인덱싱할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-236">For example, non-deterministic computed columns cannot be indexed.</span></span>  
  
 <span data-ttu-id="b635c-237">**병합 게시됨**</span><span class="sxs-lookup"><span data-stu-id="b635c-237">**Is Merge-published**</span></span>  
 <span data-ttu-id="b635c-238">열의 병합 게시 여부를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-238">Shows whether the column is merge-published.</span></span>  
  
 <span data-ttu-id="b635c-239">**복제용 아님**</span><span class="sxs-lookup"><span data-stu-id="b635c-239">**Is Not For Replication**</span></span>  
 <span data-ttu-id="b635c-240">복제하는 동안 원래 ID 값의 유지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-240">Indicates whether original identity values are preserved during replication.</span></span> <span data-ttu-id="b635c-241">이 속성을 편집하려면 해당 값을 클릭하고 드롭다운 목록을 확장한 다음 다른 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-241">To edit this property, click its value, expand the drop-down list, and choose another value.</span></span>  
  
 <span data-ttu-id="b635c-242">**복제됨**</span><span class="sxs-lookup"><span data-stu-id="b635c-242">**Is Replicated**</span></span>  
 <span data-ttu-id="b635c-243">이 열이 다른 위치에 복제되었는지 여부를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-243">Shows whether this column is replicated in another location.</span></span>  
  
 <span data-ttu-id="b635c-244">**RowGuid**</span><span class="sxs-lookup"><span data-stu-id="b635c-244">**Is RowGuid**</span></span>  
 <span data-ttu-id="b635c-245">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 열을 ROWGUID로 사용하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-245">Indicates whether [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses the column as a ROWGUID.</span></span> <span data-ttu-id="b635c-246">데이터 형식이 인 열에 대해서만이 값을 **예** 로 설정할 수 있습니다 `uniqueidentifier` .</span><span class="sxs-lookup"><span data-stu-id="b635c-246">You can set this value to **Yes** only for a column with the data type of `uniqueidentifier`.</span></span> <span data-ttu-id="b635c-247">이 속성을 편집하려면 해당 값을 클릭하고 드롭다운 목록을 확장한 다음 다른 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-247">To edit this property, click its value, expand the drop-down list, and choose another value.</span></span>  
  
 <span data-ttu-id="b635c-248">**크기**</span><span class="sxs-lookup"><span data-stu-id="b635c-248">**Size**</span></span>  
 <span data-ttu-id="b635c-249">열의 데이터 형식에 허용되는 크기(바이트)를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-249">Shows the size in bytes allowed by column's data type.</span></span> <span data-ttu-id="b635c-250">예를 들어 `nchar` 데이터 형식의 길이가 10(문자 수)까지 허용되면 유니코드 문자 집합 크기는 20까지 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-250">For example, a `nchar` data type may have a length of 10 (the number of characters) but it would have a size of 20 to account for Unicode character sets.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b635c-251">`varchar(max)` 데이터 형식의 길이는 각 행별로 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-251">The length of a `varchar(max)` data type varies for each row.</span></span> <span data-ttu-id="b635c-252">sp_help은 열 길이로 (-1)을 반환 `varchar(max)` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-252">sp_help returns (-1) as the length of `varchar(max)` column.</span></span> [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="b635c-253">는 열 크기로 -1을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b635c-253">displays -1 as the column size.</span></span>  
  
  

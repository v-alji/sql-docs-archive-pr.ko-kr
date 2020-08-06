---
title: 전체 텍스트 인덱스 열 대화 상자(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.fulltextcolumn
ms.assetid: a6f41c5c-d950-4d64-9e42-d062925917b6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7f1cd2c94739a13e1820d8c05b338abd91d8a908
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741531"
---
# <a name="full-text-index-columns-dialog-box-visual-database-tools"></a><span data-ttu-id="128f5-102">전체 텍스트 인덱스 열 대화 상자(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="128f5-102">Full-Text Index Columns Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="128f5-103">이 대화 상자에는 테이블 디자이너에 열려 있는 테이블에 대한 전체 텍스트 인덱스와 관련된 열이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="128f5-103">This dialog box lists the columns participating in the full-text index for the table open in Table Designer.</span></span> <span data-ttu-id="128f5-104">이 대화 상자를 열려면 테이블 디자이너에서 테이블을 마우스 오른쪽 단추로 클릭하고 **전체 텍스트 인덱스**를 선택한 다음, **전체 텍스트 인덱스** 대화 상자에서 보거나 편집하려는 열이 포함된 인덱스를 클릭하고 오른쪽 표에서 **열** 필드를 클릭한 후 줄임표( **...** )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="128f5-104">To access this dialog box, right-click the table in Table Designer, choose **Full-Text Index**, and in the **Full-Text Index** dialog box, click the index with columns you want to view or edit, click the **Columns** field in the grid to the right, and click the ellipses (**...**).</span></span>  
  
## <a name="options"></a><span data-ttu-id="128f5-105">옵션</span><span class="sxs-lookup"><span data-stu-id="128f5-105">Options</span></span>  
 <span data-ttu-id="128f5-106">**열**</span><span class="sxs-lookup"><span data-stu-id="128f5-106">**Column**</span></span>  
 <span data-ttu-id="128f5-107">전체 텍스트 인덱스에 관련된 열의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="128f5-107">Shows the names of columns participating in the full-text index.</span></span> <span data-ttu-id="128f5-108">열을 추가하려면 비어 있는 첫 번째 셀을 클릭하고 드롭다운 목록에서 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="128f5-108">To add a column, click in the first empty cell and choose a column from the drop-down list.</span></span> <span data-ttu-id="128f5-109">텍스트를 기반으로 한 열이나 이미지 데이터 형식의 열만 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="128f5-109">Only columns with either text-based or image data types will be accessible.</span></span>  
  
 <span data-ttu-id="128f5-110">**데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="128f5-110">**Data Type**</span></span>  
 <span data-ttu-id="128f5-111">각 열의 데이터 형식을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="128f5-111">Shows the data type for each column.</span></span> <span data-ttu-id="128f5-112">이 속성은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="128f5-112">This is a read-only property.</span></span> <span data-ttu-id="128f5-113">데이터 형식을 변경하려면 테이블 디자이너에서 테이블을 열고 열을 클릭한 다음 **열 속성** 탭에서 데이터 형식을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="128f5-113">To change a data type, open the table in Table Designer, click the column, and edit the data type in the **Column Properties** tab.</span></span>  
  
 <span data-ttu-id="128f5-114">**열로 형식화**</span><span class="sxs-lookup"><span data-stu-id="128f5-114">**Typed by Column**</span></span>  
 <span data-ttu-id="128f5-115">이 옵션은 데이터 형식이 `image`인 열에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="128f5-115">Applies only to columns with the data type `image`.</span></span> <span data-ttu-id="128f5-116">이 옵션에서 제공하는 드롭다운 목록을 사용하여 다른 열을 선택하면 선택한 열에서 현재 열의 데이터 형식을 나타내도록 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="128f5-116">Provides a drop-down list from which you can choose which of the other columns represent the data type of this column.</span></span> <span data-ttu-id="128f5-117">현재 열의 데이터 형식이 `image`가 아닌 경우 값은 없음이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="128f5-117">If this column is not of the `image` data type the value will be None.</span></span>  
  
 <span data-ttu-id="128f5-118">데이터 형식이 `image`인 열에는 Microsoft Office 파일(.doc, .xls 및 .ppt 파일), 텍스트 파일(.txt 파일), HTML 파일(.htm 파일)이 포함될 수 있고, 이 열의 데이터 형식을 이미지로 설정하면 전체 텍스트 검색을 통해 파일 내용을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="128f5-118">Columns with the data type `image` can contain Microsoft Office files (.doc, .xls, and .ppt files), text files (.txt files), and HTML files (.htm files), and setting the data type of that column to image allows the full-text search to search the contents of the files.</span></span>  
  
 <span data-ttu-id="128f5-119">**언어**</span><span class="sxs-lookup"><span data-stu-id="128f5-119">**Language**</span></span>  
 <span data-ttu-id="128f5-120">사용할 수 있는 언어를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="128f5-120">Lists available languages.</span></span> <span data-ttu-id="128f5-121">열 데이터에 해당하는 언어를 드롭다운 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="128f5-121">Choose the language from the drop-down list appropriate for your column data.</span></span> <span data-ttu-id="128f5-122">예를 들어 사용 중인 운영 체제는 영어이지만 독일어 텍스트가 포함된 열을 인덱싱하려는 경우 드롭다운 목록에서 독일어를 선택하면 인덱싱 속도를 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="128f5-122">For example, if you are using an English operating system, but you want to index a column that contains German text, choose German from the drop-down list to improve the index's performance.</span></span>  
  
 <span data-ttu-id="128f5-123">**통계 의미 체계**</span><span class="sxs-lookup"><span data-stu-id="128f5-123">**Statistical Semantics**</span></span>  
 <span data-ttu-id="128f5-124">선택한 열에 대해 의미 체계 인덱싱을 사용하도록 설정할지 여부를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="128f5-124">Select whether to enable semantic indexing for the selected column.</span></span> <span data-ttu-id="128f5-125">자세한 내용은 [의미 체계 검색&#40;SQL Server&#41;](../../relational-databases/search/semantic-search-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="128f5-125">For more information, see [Semantic Search &#40;SQL Server&#41;](../../relational-databases/search/semantic-search-sql-server.md).</span></span>  
  
 <span data-ttu-id="128f5-126">**통계 의미 체계** 를 선택하기 전에 **언어**를 선택했으며 선택한 언어에 연결된 의미 체계 언어 모델이 없으면 **통계 의미 체계** 확인란은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="128f5-126">If you select a **Language** prior to selecting **Statistical Semantics**, and the selected language does not have an associated Semantic Language Model, then the **Statistical Semantics** checkbox is disabled.</span></span> <span data-ttu-id="128f5-127">**언어** 를 선택하기 전에 **통계 의미 체계**를 선택한 경우 드롭다운 콤보 상자에서 사용할 수 있는 언어가 의미 체계 언어 모델에서 지원하는 언어로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="128f5-127">If you select **Statistical Semantics** prior to selecting a **Language**, the languages available in the drop-down combo box will be restricted to those for which there is Semantic Language Model support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="128f5-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="128f5-128">See Also</span></span>  
 [<span data-ttu-id="128f5-129">전체 텍스트 인덱스 대화 상자&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="128f5-129">Full-Text Index Dialog Box &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  

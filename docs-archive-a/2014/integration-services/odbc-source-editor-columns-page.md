---
title: ODBC 원본 편집기 (열 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.columns.f1
ms.assetid: 565984eb-8318-4be7-bebc-262209cf5065
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7a11ab6a86978366d07fbe63362f1702310b5d89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734359"
---
# <a name="odbc-source-editor-columns-page"></a><span data-ttu-id="e905b-102">ODBC 원본 편집기(열 페이지)</span><span class="sxs-lookup"><span data-stu-id="e905b-102">ODBC Source Editor (Columns Page)</span></span>
  <span data-ttu-id="e905b-103">**ODBC 원본 편집기** 대화 상자의 **열** 페이지를 사용하여 출력 열을 각 외부(원본) 열에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e905b-103">Use the **Columns** page of the **ODBC Source Editor** dialog box to map an output column to each external (source) column.</span></span>  
  
 <span data-ttu-id="e905b-104">ODBC 원본에 대한 자세한 내용은 [ODBC Source](data-flow/odbc-source.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e905b-104">To learn more about the ODBC source, see [ODBC Source](data-flow/odbc-source.md).</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="e905b-105">작업 목록</span><span class="sxs-lookup"><span data-stu-id="e905b-105">Task List</span></span>  
 <span data-ttu-id="e905b-106">**ODBC 원본 편집기의 열 페이지를 열려면**</span><span class="sxs-lookup"><span data-stu-id="e905b-106">**To open the ODBC Source Editor Columns Page**</span></span>  
  
1.  <span data-ttu-id="e905b-107">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 ODBC 원본이 있는 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e905b-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the ODBC source.</span></span>  
  
2.  <span data-ttu-id="e905b-108">**데이터 흐름** 탭에서 ODBC 원본을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e905b-108">On the **Data Flow** tab, double-click the ODBC source.</span></span>  
  
3.  <span data-ttu-id="e905b-109">**ODBC 원본 편집기**에서 **열**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e905b-109">In the **ODBC Source Editor**, click **Columns**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e905b-110">옵션</span><span class="sxs-lookup"><span data-stu-id="e905b-110">Options</span></span>  
  
### <a name="available-external-columns"></a><span data-ttu-id="e905b-111">사용 가능한 외부 열</span><span class="sxs-lookup"><span data-stu-id="e905b-111">Available External Columns</span></span>  
 <span data-ttu-id="e905b-112">데이터 원본에서 사용 가능한 외부 열의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="e905b-112">A list of available external columns in the data source.</span></span> <span data-ttu-id="e905b-113">이 테이블을 사용하여 열을 추가하거나 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e905b-113">You cannot use this table to add or delete columns.</span></span> <span data-ttu-id="e905b-114">원본에서 사용할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e905b-114">Select the columns to use from the source.</span></span> <span data-ttu-id="e905b-115">선택한 열이 선택 순서대로 **외부 열** 목록에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="e905b-115">The selected columns are added to the **External Column** list in the order they are selected.</span></span>  
  
 <span data-ttu-id="e905b-116">모든 열을 선택하려면 **모두 선택** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e905b-116">Select the **Select All** check box to select all of the columns.</span></span>  
  
### <a name="external-column"></a><span data-ttu-id="e905b-117">외부 열</span><span class="sxs-lookup"><span data-stu-id="e905b-117">External Column</span></span>  
 <span data-ttu-id="e905b-118">ODBC 원본의 데이터를 사용하는 구성 요소를 구성할 때 표시되는 순서로 된 외부(원본) 열의 뷰입니다.</span><span class="sxs-lookup"><span data-stu-id="e905b-118">A view of the external (source) columns in the order that you see them when configuring components that consume data from the ODBC source.</span></span>  
  
### <a name="output-column"></a><span data-ttu-id="e905b-119">출력 열</span><span class="sxs-lookup"><span data-stu-id="e905b-119">Output Column</span></span>  
 <span data-ttu-id="e905b-120">각 출력 열의 고유 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e905b-120">Enter a unique name for each output column.</span></span> <span data-ttu-id="e905b-121">기본값은 선택한 외부(원본) 열의 이름이지만 설명이 포함된 고유 이름을 임의로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e905b-121">The default is the name of the selected external (source) column; however, you can choose any unique, descriptive name.</span></span> <span data-ttu-id="e905b-122">입력한 이름은 SSIS 디자이너에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e905b-122">The name entered is displayed in the SSIS Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e905b-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e905b-123">See Also</span></span>  
 <span data-ttu-id="e905b-124">[ODBC 원본 편집기 &#40;연결 관리자 페이지&#41;](../../2014/integration-services/odbc-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="e905b-124">[ODBC Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/odbc-source-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="e905b-125">ODBC 원본 편집기&#40;오류 출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="e905b-125">ODBC Source Editor &#40;Error Output Page&#41;</span></span>](../../2014/integration-services/odbc-source-editor-error-output-page.md)  
  
  

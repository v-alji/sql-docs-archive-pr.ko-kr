---
title: ADO NET 원본 편집기 (열 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetsource.columns.f1
ms.assetid: fbc205b9-2001-4737-a76b-1ba777344bd9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0d89f8c926761b9149f19269bc2519c12bcf130e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651231"
---
# <a name="ado-net-source-editor-columns-page"></a><span data-ttu-id="4ef98-102">ADO NET 원본 편집기(열 페이지)</span><span class="sxs-lookup"><span data-stu-id="4ef98-102">ADO NET Source Editor (Columns Page)</span></span>
  <span data-ttu-id="4ef98-103">**ADO NET 원본 편집기** 대화 상자의 **열** 페이지를 사용하여 출력 열을 각 외부(원본) 열에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ef98-103">Use the **Columns** page of the **ADO NET Source Editor** dialog box to map an output column to each external (source) column.</span></span>  
  
 <span data-ttu-id="4ef98-104">ADO NET 원본에 대한 자세한 내용은 [ADO NET Source](data-flow/ado-net-source.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4ef98-104">To learn more about the ADO NET source, see [ADO NET Source](data-flow/ado-net-source.md).</span></span>  
  
 <span data-ttu-id="4ef98-105">**열 페이지를 열려면**</span><span class="sxs-lookup"><span data-stu-id="4ef98-105">**To open the Columns page**</span></span>  
  
1.  <span data-ttu-id="4ef98-106">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 ADO NET 원본이 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4ef98-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that has the ADO NET source.</span></span>  
  
2.  <span data-ttu-id="4ef98-107">**데이터 흐름** 탭에서 ADO NET 원본을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4ef98-107">On the **Data Flow** tab, double-click the ADO NET source.</span></span>  
  
3.  <span data-ttu-id="4ef98-108">**ADO NET 원본 편집기**에서 **열**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4ef98-108">In the **ADO NET Source Editor**, click **Columns**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4ef98-109">옵션</span><span class="sxs-lookup"><span data-stu-id="4ef98-109">Options</span></span>  
 <span data-ttu-id="4ef98-110">**사용 가능한 외부 열**</span><span class="sxs-lookup"><span data-stu-id="4ef98-110">**Available External Columns**</span></span>  
 <span data-ttu-id="4ef98-111">데이터 원본에서 사용 가능한 외부 열의 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4ef98-111">View the list of available external columns in the data source.</span></span> <span data-ttu-id="4ef98-112">이 테이블을 사용하여 열을 추가하거나 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4ef98-112">You cannot use this table to add or delete columns.</span></span>  
  
 <span data-ttu-id="4ef98-113">**외부 열**</span><span class="sxs-lookup"><span data-stu-id="4ef98-113">**External Column**</span></span>  
 <span data-ttu-id="4ef98-114">이 원본의 데이터를 사용하는 구성 요소를 구성할 때 표시되는 순서로 외부(원본) 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4ef98-114">View external (source) columns in the order in which you will see them when configuring components that consume data from this source.</span></span>  
  
 <span data-ttu-id="4ef98-115">**출력 열**</span><span class="sxs-lookup"><span data-stu-id="4ef98-115">**Output Column**</span></span>  
 <span data-ttu-id="4ef98-116">각 출력 열에 고유한 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4ef98-116">Provide a unique name for each output column.</span></span> <span data-ttu-id="4ef98-117">기본값은 선택한 외부(원본) 열의 이름이지만 설명이 포함된 고유 이름을 임의로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ef98-117">The default is the name of the selected external (source) column; however, you can choose any unique, descriptive name.</span></span> <span data-ttu-id="4ef98-118">제공한 이름은 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ef98-118">The name provided will be displayed within the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ef98-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4ef98-119">See Also</span></span>  
 <span data-ttu-id="4ef98-120">[ADO NET 원본 편집기 &#40;연결 관리자 페이지&#41;](../../2014/integration-services/ado-net-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="4ef98-120">[ADO NET Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/ado-net-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="4ef98-121">[ADO NET 원본 편집기 &#40;오류 출력 페이지&#41;](../../2014/integration-services/ado-net-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="4ef98-121">[ADO NET Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/ado-net-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="4ef98-122">ADO.NET 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="4ef98-122">ADO.NET Connection Manager</span></span>](connection-manager/ado-net-connection-manager.md)  
  
  

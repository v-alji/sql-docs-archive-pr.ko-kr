---
title: 열 복사 변환 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.copymaptransformation.f1
helpviewer_keywords:
- Copy Column Transformation Editor
ms.assetid: d8e70541-d563-4ce4-bf66-bc888a0d3026
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7647d25891b37e5f09356d427072e84b45882e4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651833"
---
# <a name="copy-column-transformation-editor"></a><span data-ttu-id="880ce-102">열 복사 변환 편집기</span><span class="sxs-lookup"><span data-stu-id="880ce-102">Copy Column Transformation Editor</span></span>
  <span data-ttu-id="880ce-103">**열 복사 변환 편집기** 대화 상자를 사용하여 복사할 열을 선택하고 새 출력 열의 이름을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="880ce-103">Use the **Copy Column Transformation Editor** dialog box to select columns to copy and to assign names for the new output columns.</span></span>  
  
 <span data-ttu-id="880ce-104">열 복사 변환에 대한 자세한 내용은 [Copy Column Transformation](data-flow/transformations/copy-column-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="880ce-104">To learn more about the Copy Column transformation, see [Copy Column Transformation](data-flow/transformations/copy-column-transformation.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="880ce-105">사용자가 모든 원본 데이터를 대상에 간단하게 복사할 경우 열 복사 변환을 사용할 필요가 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="880ce-105">When you are simply copying all of your source data to a destination, it may not be necessary to use the Copy Column transformation.</span></span> <span data-ttu-id="880ce-106">일부 시나리오에서는 데이터 변환이 필요하지 않을 때 원본을 대상에 직접 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="880ce-106">In some scenarios, you can connect a source directly to a destination, when no data transformation is required.</span></span> <span data-ttu-id="880ce-107">이러한 상황에서는 SQL Server 가져오기 및 내보내기 마법사를 사용하여 패키지를 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="880ce-107">In these circumstances it is often preferable to use the SQL Server Import and Export Wizard to create your package for you.</span></span> <span data-ttu-id="880ce-108">필요한 경우 나중에 패키지를 향상시키고 다시 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="880ce-108">Later you can enhance and reconfigure the package as needed.</span></span> <span data-ttu-id="880ce-109">자세한 내용은 [SQL Server Import and Export Wizard](import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="880ce-109">For more information, see [SQL Server Import and Export Wizard](import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="880ce-110">옵션</span><span class="sxs-lookup"><span data-stu-id="880ce-110">Options</span></span>  
 <span data-ttu-id="880ce-111">**사용 가능한 입력 열**</span><span class="sxs-lookup"><span data-stu-id="880ce-111">**Available Input Columns**</span></span>  
 <span data-ttu-id="880ce-112">확인란을 사용하여 복사할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="880ce-112">Select columns to copy by using the check boxes.</span></span> <span data-ttu-id="880ce-113">선택한 항목은 아래의 입력 열에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="880ce-113">Your selections add input columns to the table below.</span></span>  
  
 <span data-ttu-id="880ce-114">**입력 열**</span><span class="sxs-lookup"><span data-stu-id="880ce-114">**Input Column**</span></span>  
 <span data-ttu-id="880ce-115">사용 가능한 입력 열 목록에서 복사할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="880ce-115">Select columns to copy from the list of available input columns.</span></span> <span data-ttu-id="880ce-116">선택 내용에 따라 **사용 가능한 입력 열** 테이블의 확인란이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="880ce-116">Your selections are reflected in the check box selections in the **Available Input Columns** table.</span></span>  
  
 <span data-ttu-id="880ce-117">**출력 별칭**</span><span class="sxs-lookup"><span data-stu-id="880ce-117">**Output Alias**</span></span>  
 <span data-ttu-id="880ce-118">각 새 출력 열의 별칭을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="880ce-118">Type an alias for each new output column.</span></span> <span data-ttu-id="880ce-119">기본값은 **사본 -** 뒤에 입력 열의 이름이 오는 형식이지만 설명이 포함된 고유 이름을 임의로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="880ce-119">The default is **Copy of**, followed by the name of the input column; however, you can choose any unique, descriptive name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="880ce-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="880ce-120">See Also</span></span>  
 [<span data-ttu-id="880ce-121">Integration Services 오류 및 메시지 참조</span><span class="sxs-lookup"><span data-stu-id="880ce-121">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  

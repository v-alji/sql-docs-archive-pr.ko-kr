---
title: 열 선택 대화 상자 (마이닝 구조 뷰) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.structure.addacolumn.f1
helpviewer_keywords:
- Select a Column dialog box
ms.assetid: 6f73a7dc-5401-40c3-8f1d-b41fc1dd91c2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9f8efedd768ed90c039d2799ef66ff02f7c2f37c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647903"
---
# <a name="select-a-column-dialog-box-mining-structure-view"></a><span data-ttu-id="64f4c-102">열 선택 대화 상자(마이닝 구조 뷰)</span><span class="sxs-lookup"><span data-stu-id="64f4c-102">Select a Column Dialog Box (Mining Structure View)</span></span>
  <span data-ttu-id="64f4c-103">**열 선택** 대화 상자를 사용하여 마이닝 구조에 열을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64f4c-103">Use the **Select a Column** dialog box to add columns to the mining structure.</span></span> <span data-ttu-id="64f4c-104">이 대화 상자는 OLAP 마이닝 모델로 작업을 수행하는지, 아니면 관계형 마이닝 모델로 작업을 수행하는지에 따라 옵션이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="64f4c-104">The dialog contains different options depending on whether you are working with an OLAP mining model or a relational mining model.</span></span>  
  
## <a name="options"></a><span data-ttu-id="64f4c-105">옵션</span><span class="sxs-lookup"><span data-stu-id="64f4c-105">Options</span></span>  
 <span data-ttu-id="64f4c-106">**원본 테이블**</span><span class="sxs-lookup"><span data-stu-id="64f4c-106">**Source table**</span></span>  
 <span data-ttu-id="64f4c-107">마이닝 모델의 기반이 되는 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="64f4c-107">The table on which the mining model is based.</span></span>  
  
 <span data-ttu-id="64f4c-108">이 옵션은 관계형 마이닝 모델에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="64f4c-108">This option is only used for relational mining models.</span></span>  
  
 <span data-ttu-id="64f4c-109">**원본 열**</span><span class="sxs-lookup"><span data-stu-id="64f4c-109">**Source column**</span></span>  
 <span data-ttu-id="64f4c-110">마이닝 구조에 추가할 수 있는 원본 테이블의 사용 가능한 모든 열 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="64f4c-110">A list of all the available columns in the source table that you can add to the mining structure.</span></span>  
  
 <span data-ttu-id="64f4c-111">이 옵션은 관계형 마이닝 모델에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="64f4c-111">This option is only used for relational mining models.</span></span>  
  
 <span data-ttu-id="64f4c-112">**열 유형 표시**</span><span class="sxs-lookup"><span data-stu-id="64f4c-112">**Show column types**</span></span>  
 <span data-ttu-id="64f4c-113">사용 가능한 열 데이터 형식의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="64f4c-113">A list of available column data types.</span></span> <span data-ttu-id="64f4c-114">**원본 열**의 열 목록을 필터링할 데이터 형식을 선택하거나 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="64f4c-114">Select or clear data types to filter the list of columns in **Source column**.</span></span> <span data-ttu-id="64f4c-115">선택한 데이터 형식과 일치하는 열만 **원본 열** 목록에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="64f4c-115">Only columns that match the checked data types will be shown in the **Source column** list.</span></span>  
  
 <span data-ttu-id="64f4c-116">이 옵션은 관계형 마이닝 모델에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="64f4c-116">This option is only used for relational mining models.</span></span>  
  
 <span data-ttu-id="64f4c-117">**관련 특성 및 측정값**</span><span class="sxs-lookup"><span data-stu-id="64f4c-117">**Related attributes and measures**</span></span>  
 <span data-ttu-id="64f4c-118">마이닝 구조에 추가할 수 있는 사용 가능한 모든 측정값 및 특성 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="64f4c-118">A list of all the available measures and attributes that you can add to the mining structure.</span></span>  
  
 <span data-ttu-id="64f4c-119">이 옵션은 OLAP 마이닝 모델에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="64f4c-119">This option is only used for OLAP mining models.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64f4c-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="64f4c-120">See Also</span></span>  
 <span data-ttu-id="64f4c-121">[마이닝 구조 뷰 &#40;데이터 마이닝 모델 디자이너&#41;](mining-structure-view-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="64f4c-121">[Mining Structure View &#40;Data Mining Model Designer&#41;](mining-structure-view-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="64f4c-122">마이닝 구조에 열 추가</span><span class="sxs-lookup"><span data-stu-id="64f4c-122">Add Columns to a Mining Structure</span></span>](data-mining/add-columns-to-a-mining-structure.md)  
  
  

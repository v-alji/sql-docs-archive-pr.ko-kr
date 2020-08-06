---
title: 중첩 테이블 키 열 선택 대화 상자 (마이닝 구조 뷰) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.structure.addnestedtable.f1
helpviewer_keywords:
- Select a Nested Table Key Column dialog box
ms.assetid: f68b89a7-17df-45f8-ba7f-b458cd9b1ec3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4dc524f6913b7be15e87869355515397a3e0b65c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653564"
---
# <a name="select-a-nested-table-key-column-dialog-box-mining-structure-view"></a><span data-ttu-id="98e41-102">중첩 테이블 키 열 선택 대화 상자(마이닝 구조 뷰)</span><span class="sxs-lookup"><span data-stu-id="98e41-102">Select a Nested Table Key Column Dialog Box (Mining Structure View)</span></span>
  <span data-ttu-id="98e41-103">**중첩 테이블 키 열 선택** 대화 상자를 사용하여 새 중첩 테이블의 키 역할을 할 열을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98e41-103">Use the **Select a Nested Table Key Column** dialog box to designate a column that will act as the key for the new nested table.</span></span> <span data-ttu-id="98e41-104">대화 상자를 종료하면 지정된 키 열을 포함하는 새 테이블이 마이닝 구조에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="98e41-104">When you exit the dialog box, a new table is added to the mining structure that contains the designated key column.</span></span> <span data-ttu-id="98e41-105">구조를 마우스 오른쪽 단추로 클릭한 다음 **열 추가**를 선택하여 중첩 테이블에 열을 더 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98e41-105">You can add additional columns to the nested table by right-clicking the structure and selecting **Add a Column**.</span></span> <span data-ttu-id="98e41-106">이 대화 상자는 OLAP 마이닝 모델로 작업을 수행하는지, 아니면 관계형 마이닝 모델로 작업을 수행하는지에 따라 옵션이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="98e41-106">The dialog box contains different options depending on whether you are working with an OLAP mining model or a relational mining model.</span></span>  
  
## <a name="options"></a><span data-ttu-id="98e41-107">옵션</span><span class="sxs-lookup"><span data-stu-id="98e41-107">Options</span></span>  
 <span data-ttu-id="98e41-108">**원본 테이블**</span><span class="sxs-lookup"><span data-stu-id="98e41-108">**Source table**</span></span>  
 <span data-ttu-id="98e41-109">마이닝 모델의 기반이 되는 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="98e41-109">The table on which the mining model is based.</span></span>  
  
 <span data-ttu-id="98e41-110">이 옵션은 관계형 마이닝 모델에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="98e41-110">This is only used for relational mining models.</span></span>  
  
 <span data-ttu-id="98e41-111">**원본 열**</span><span class="sxs-lookup"><span data-stu-id="98e41-111">**Source column**</span></span>  
 <span data-ttu-id="98e41-112">중첩 테이블의 키로 사용할 수 있는 원본 테이블의 사용 가능한 모든 열 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="98e41-112">A list of all the available columns in the source table that you can use as the key of the nested table.</span></span>  
  
 <span data-ttu-id="98e41-113">이 옵션은 관계형 마이닝 모델에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="98e41-113">This is only used for relational mining models.</span></span>  
  
 <span data-ttu-id="98e41-114">**열 유형 표시**</span><span class="sxs-lookup"><span data-stu-id="98e41-114">**Show column types**</span></span>  
 <span data-ttu-id="98e41-115">사용 가능한 열 데이터 형식의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="98e41-115">A list of available column data types.</span></span> <span data-ttu-id="98e41-116">**원본 열**의 열 목록을 필터링할 데이터 형식을 선택하거나 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="98e41-116">Select or clear data types to filter the list of columns in **Source column**.</span></span> <span data-ttu-id="98e41-117">선택한 데이터 형식과 일치하는 열만 **원본 열** 목록에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98e41-117">Only columns that match the checked data types will be shown in the **Source column** list.</span></span>  
  
 <span data-ttu-id="98e41-118">이 옵션은 관계형 마이닝 모델에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="98e41-118">This is only used for relational mining models.</span></span>  
  
 <span data-ttu-id="98e41-119">**특성**</span><span class="sxs-lookup"><span data-stu-id="98e41-119">**Attributes**</span></span>  
 <span data-ttu-id="98e41-120">중첩 테이블의 키로 사용할 수 있는 특성 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="98e41-120">A list of attributes that you can use as the key of the nested table.</span></span>  
  
 <span data-ttu-id="98e41-121">이 옵션은 OLAP 마이닝 모델에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="98e41-121">This is only used for OLAP mining models.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98e41-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="98e41-122">See Also</span></span>  
 [<span data-ttu-id="98e41-123">마이닝 구조 뷰 &#40;데이터 마이닝 모델 디자이너&#41;</span><span class="sxs-lookup"><span data-stu-id="98e41-123">Mining Structure View &#40;Data Mining Model Designer&#41;</span></span>](mining-structure-view-data-mining-model-designer.md)  
  
  

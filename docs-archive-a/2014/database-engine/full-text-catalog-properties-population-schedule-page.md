---
title: 전체 텍스트 카탈로그 속성 (채우기 일정 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftcatalogproperties.schedule.f1
ms.assetid: 8681506b-5dc6-4165-beb6-1e76ca470425
author: rothja
ms.author: jroth
ms.openlocfilehash: 62d69cdc42745fcbb5eb7d2cb05f90b710e5c70d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740299"
---
# <a name="full-text-catalog-properties-population-schedule-page"></a><span data-ttu-id="b5cb5-102">전체 텍스트 카탈로그 속성(채우기 일정 페이지)</span><span class="sxs-lookup"><span data-stu-id="b5cb5-102">Full-Text Catalog Properties (Population Schedule Page)</span></span>
  <span data-ttu-id="b5cb5-103">이 대화 상자를 사용하여 전체 텍스트 카탈로그를 채우거나 다시 채우는 시기를 결정하는 일정을 추가하거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5cb5-103">Use this dialog box to add or modify schedules that determine when the full-text catalog will be populated or repopulated.</span></span>  
  
## <a name="schedules-grid"></a><span data-ttu-id="b5cb5-104">일정 표</span><span class="sxs-lookup"><span data-stu-id="b5cb5-104">Schedules Grid</span></span>  
 <span data-ttu-id="b5cb5-105">각 행은 카탈로그를 채우거나 다시 채우도록 예약된 작업을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b5cb5-105">Each row represents a scheduled operation to populate or repopulate the catalog.</span></span>  
  
 <span data-ttu-id="b5cb5-106">**이름**</span><span class="sxs-lookup"><span data-stu-id="b5cb5-106">**Name**</span></span>  
 <span data-ttu-id="b5cb5-107">일정 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b5cb5-107">Displays the name of the schedule.</span></span>  
  
 <span data-ttu-id="b5cb5-108">**채우기 유형**</span><span class="sxs-lookup"><span data-stu-id="b5cb5-108">**Population Type**</span></span>  
 <span data-ttu-id="b5cb5-109">전체, 증분 또는 최적화 등의 채우기 작업을 표시하거나 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="b5cb5-109">View or modify the population operation: full, incremental or an optimization operation.</span></span>  
  
 <span data-ttu-id="b5cb5-110">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="b5cb5-110">**Enabled**</span></span>  
 <span data-ttu-id="b5cb5-111">예약된 작업을 사용하려면 이 확인란을 선택하고 사용하지 않으려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="b5cb5-111">Select or clear this checkbox to enable or disable the scheduled operation.</span></span>  
  
 <span data-ttu-id="b5cb5-112">**설명**</span><span class="sxs-lookup"><span data-stu-id="b5cb5-112">**Description**</span></span>  
 <span data-ttu-id="b5cb5-113">예약된 작업에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="b5cb5-113">Description of the scheduled operation.</span></span>  
  
 <span data-ttu-id="b5cb5-114">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="b5cb5-114">**New**</span></span>  
 <span data-ttu-id="b5cb5-115">새 인덱싱 일정을 만들려면 이 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5cb5-115">Click this button to create a new indexing schedule.</span></span> <span data-ttu-id="b5cb5-116">이 단추를 클릭하면 **새 전체 텍스트 인덱싱 카탈로그 일정** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5cb5-116">This button brings up the **New Full-Text Indexing Catalog Schedule** dialog box.</span></span>  
  
 <span data-ttu-id="b5cb5-117">**편집**</span><span class="sxs-lookup"><span data-stu-id="b5cb5-117">**Edit**</span></span>  
 <span data-ttu-id="b5cb5-118">선택한 채우기 일정을 편집하려면 이 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5cb5-118">Click this button to edit the selected population schedule.</span></span>  
  
 <span data-ttu-id="b5cb5-119">**삭제**</span><span class="sxs-lookup"><span data-stu-id="b5cb5-119">**Delete**</span></span>  
 <span data-ttu-id="b5cb5-120">선택한 채우기 일정을 제거하려면 이 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5cb5-120">Click this button to remove the selected population schedule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5cb5-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b5cb5-121">See Also</span></span>  
 [<span data-ttu-id="b5cb5-122">CREATE FULLTEXT CATALOG&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b5cb5-122">CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-catalog-transact-sql)  
  
  

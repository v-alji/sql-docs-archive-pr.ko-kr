---
title: 전체 텍스트 인덱스 속성 (일정 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.fulltextindexproperties.schedule.f1
ms.assetid: a828e284-097e-4854-8c49-931934eb73bf
author: rothja
ms.author: jroth
ms.openlocfilehash: f49fb37295f0b3eb2f1a2dd04d44ab86236f109a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661305"
---
# <a name="full-text-index-properties-schedules-page"></a><span data-ttu-id="0b8a4-102">전체 텍스트 인덱스 속성(일정 페이지)</span><span class="sxs-lookup"><span data-stu-id="0b8a4-102">Full-Text Index Properties (Schedules Page)</span></span>
  <span data-ttu-id="0b8a4-103">이 페이지를 사용하여 전체 텍스트 인덱스의 기본 테이블에 대한 업데이트의 증분 채우기를 시작하는 SQL Server 에이전트 작업을 실행하는 일정을 보거나 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b8a4-103">Use this page to view and create schedules for running a SQL Server Agent job that starts an incremental population of updates to the base table of the full-text index.</span></span> <span data-ttu-id="0b8a4-104">기본 테이블이나 뷰에 `timestamp` 데이터 형식의 열이 포함되어 있지 않으면 전체 채우기가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b8a4-104">If the base table or view does not contain a column of the `timestamp` data type, a full population is performed.</span></span>  
  
 <span data-ttu-id="0b8a4-105">**전체 텍스트 인덱스의 속성을 보거나 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="0b8a4-105">**To view or change the properties of a full-text index**</span></span>  
  
-   [<span data-ttu-id="0b8a4-106">전체 텍스트 인덱스 관리</span><span class="sxs-lookup"><span data-stu-id="0b8a4-106">Manage Full-Text Indexes</span></span>](../relational-databases/indexes/indexes.md)  
  
## <a name="ui-element-list"></a><span data-ttu-id="0b8a4-107">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="0b8a4-107">UI element list</span></span>  
 <span data-ttu-id="0b8a4-108">**일정**</span><span class="sxs-lookup"><span data-stu-id="0b8a4-108">**Schedules**</span></span>  
 <span data-ttu-id="0b8a4-109">전체 텍스트 인덱스의 기본 테이블에 대해 예약된 각 증분 채우기(있는 경우)를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="0b8a4-109">Lists each scheduled incremental population, if any, on the base table for the full-text index.</span></span>  
  
 <span data-ttu-id="0b8a4-110">**이름**</span><span class="sxs-lookup"><span data-stu-id="0b8a4-110">**Name**</span></span>  
 <span data-ttu-id="0b8a4-111">예약된 각 채우기의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0b8a4-111">Displays the name of the each scheduled population.</span></span>  
  
 <span data-ttu-id="0b8a4-112">**채우기 유형**</span><span class="sxs-lookup"><span data-stu-id="0b8a4-112">**Population Type**</span></span>  
 <span data-ttu-id="0b8a4-113">예약된 각 채우기의 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0b8a4-113">Displays the type of each scheduled population.</span></span>  
  
 <span data-ttu-id="0b8a4-114">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="0b8a4-114">**Enabled**</span></span>  
 <span data-ttu-id="0b8a4-115">예약된 채우기가 현재 사용되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0b8a4-115">Indicates whether the scheduled population is currently enabled or disabled.</span></span>  
  
 <span data-ttu-id="0b8a4-116">**설명**</span><span class="sxs-lookup"><span data-stu-id="0b8a4-116">**Description**</span></span>  
 <span data-ttu-id="0b8a4-117">예약을 만들 때 지정한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0b8a4-117">Displays the description that was specified when the schedule was created.</span></span>  
  
 <span data-ttu-id="0b8a4-118">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="0b8a4-118">**New**</span></span>  
 <span data-ttu-id="0b8a4-119">전체 텍스트 인덱스를 채우는 일정을 새로 만들려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0b8a4-119">Click to create a new schedule for populating the full-text index.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b8a4-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0b8a4-120">See Also</span></span>  
 <span data-ttu-id="0b8a4-121">[전체 텍스트 인덱싱 마법사 사용](../relational-databases/search/use-the-full-text-indexing-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="0b8a4-121">[Use the Full-Text Indexing Wizard](../relational-databases/search/use-the-full-text-indexing-wizard.md) </span></span>  
 [<span data-ttu-id="0b8a4-122">전체 텍스트 인덱스 채우기</span><span class="sxs-lookup"><span data-stu-id="0b8a4-122">Populate Full-Text Indexes</span></span>](../relational-databases/search/populate-full-text-indexes.md)  
  
  

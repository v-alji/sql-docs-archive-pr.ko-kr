---
title: 지원 되지 않는 전체 텍스트 검색 속성을 사용 하는 저장 프로시저 수정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- discontinued properties [Full-Text Search]
- stored procedures [Full-Text Search]
ms.assetid: 8d9392d9-a9ba-4378-84e4-59f516b67ddb
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 12262a588742f0e3be094e32a2a0208a85b6f28a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650468"
---
# <a name="modify-stored-procedures-that-use-discontinued-full-text-search-properties"></a><span data-ttu-id="8b4a9-102">지원되지 않는 전체 텍스트 검색 속성을 사용하는 저장 프로시저를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b4a9-102">Modify stored procedures that use discontinued Full-Text Search properties</span></span>
  <span data-ttu-id="8b4a9-103">저장 프로시저가 올바로 수행되도록 하려면 기존 프로시저를 편집하고 제거되었거나 지원되지 않는 전체 텍스트 관련 속성 및 설정을 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b4a9-103">To ensure that your stored procedures perform correctly, you should edit existing procedures and remove those full-text related properties and settings that have been removed or deprecated.</span></span>  
  
## <a name="component"></a><span data-ttu-id="8b4a9-104">구성 요소</span><span class="sxs-lookup"><span data-stu-id="8b4a9-104">Component</span></span>  
 <span data-ttu-id="8b4a9-105">전체 텍스트 검색</span><span class="sxs-lookup"><span data-stu-id="8b4a9-105">Full-Text Search</span></span>  
  
## <a name="description"></a><span data-ttu-id="8b4a9-106">Description</span><span class="sxs-lookup"><span data-stu-id="8b4a9-106">Description</span></span>  
 <span data-ttu-id="8b4a9-107">제거된 전체 텍스트 검색 관련 속성 및 설정은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8b4a9-107">The following Full-Text Search-related properties and settings have been removed.</span></span>  
  
-   <span data-ttu-id="8b4a9-108">**DataTimeout**</span><span class="sxs-lookup"><span data-stu-id="8b4a9-108">**DataTimeout**</span></span>  
  
-   <span data-ttu-id="8b4a9-109">**ConnectTimeout**</span><span class="sxs-lookup"><span data-stu-id="8b4a9-109">**ConnectTimeout**</span></span>  
  
-   <span data-ttu-id="8b4a9-110">**Clean_up**</span><span class="sxs-lookup"><span data-stu-id="8b4a9-110">**Clean_up**</span></span>  
  
-   <span data-ttu-id="8b4a9-111">**LogSize**</span><span class="sxs-lookup"><span data-stu-id="8b4a9-111">**LogSize**</span></span>  
  
 <span data-ttu-id="8b4a9-112">제거되었거나 지원되지 않는 전체 텍스트 검색 관련 속성 및 설정은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8b4a9-112">The following Full-Text Search-related properties and settings have been removed or deprecated:</span></span>  
  
-   <span data-ttu-id="8b4a9-113">전체 텍스트 카탈로그의 '경로'.</span><span class="sxs-lookup"><span data-stu-id="8b4a9-113">'Path' of the Full-Text Catalog.</span></span> <span data-ttu-id="8b4a9-114">전체 텍스트 카탈로그는 특정 파일 시스템 경로가 없는 논리 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="8b4a9-114">The Full-Text Catalog will be a logic object without a specific file path in the system.</span></span>  
  
-   <span data-ttu-id="8b4a9-115">SP_FULLTEXT_DATABASE의 설정/해제 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]에서는 데이터베이스에 대해 전체 텍스트 검색이 기본적으로 항상 사용되도록 설정되기 때문에 이 설정의 영향을 더 이상 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8b4a9-115">Enable/disable in SP_FULLTEXT_DATABASE has no effect anymore as databases are enabled for Full-Text Search at all times and by default in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="8b4a9-116">수정 동작</span><span class="sxs-lookup"><span data-stu-id="8b4a9-116">Corrective Action</span></span>  
 <span data-ttu-id="8b4a9-117">이러한 속성을 제거하도록 저장 프로시저를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b4a9-117">Modify your stored procedures to remove these properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b4a9-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8b4a9-118">See Also</span></span>  
 [<span data-ttu-id="8b4a9-119">업그레이드 관리자 작업</span><span class="sxs-lookup"><span data-stu-id="8b4a9-119">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  

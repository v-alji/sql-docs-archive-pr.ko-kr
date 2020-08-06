---
title: MSSQLSERVER_125 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "125"
helpviewer_keywords:
- 125 (Database Engine error)
ms.assetid: 0f58338d-2ea0-48b8-8a20-c438b0940433
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 59c732d80ccfafc8f242bb1c42fe60e3dea81f19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651042"
---
# <a name="mssqlserver_125"></a><span data-ttu-id="2a0b6-102">MSSQLSERVER_125</span><span class="sxs-lookup"><span data-stu-id="2a0b6-102">MSSQLSERVER_125</span></span>
    
## <a name="details"></a><span data-ttu-id="2a0b6-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="2a0b6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2a0b6-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="2a0b6-104">Product Name</span></span>|<span data-ttu-id="2a0b6-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2a0b6-105">SQL Server</span></span>|  
|<span data-ttu-id="2a0b6-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="2a0b6-106">Event ID</span></span>|<span data-ttu-id="2a0b6-107">125</span><span class="sxs-lookup"><span data-stu-id="2a0b6-107">125</span></span>|  
|<span data-ttu-id="2a0b6-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="2a0b6-108">Event Source</span></span>|<span data-ttu-id="2a0b6-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2a0b6-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2a0b6-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="2a0b6-110">Component</span></span>|<span data-ttu-id="2a0b6-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2a0b6-111">SQLEngine</span></span>|  
|<span data-ttu-id="2a0b6-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="2a0b6-112">Symbolic Name</span></span>||  
|<span data-ttu-id="2a0b6-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="2a0b6-113">Message Text</span></span>|<span data-ttu-id="2a0b6-114">CASE 식은 수준 %d까지만 중첩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a0b6-114">Case expressions may only be nested to level %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2a0b6-115">설명</span><span class="sxs-lookup"><span data-stu-id="2a0b6-115">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="2a0b6-116">에서는 CASE 식의 중첩을 10개 수준까지만 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="2a0b6-116">allows for only 10 levels of nesting in CASE expressions.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2a0b6-117">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="2a0b6-117">User Action</span></span>  
 <span data-ttu-id="2a0b6-118">CASE 문의 수준을 10개 이하로 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="2a0b6-118">Reduce the level of CASE statements to 10 or less.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a0b6-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2a0b6-119">See Also</span></span>  
 [<span data-ttu-id="2a0b6-120">CASE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2a0b6-120">CASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/case-transact-sql)  
  
  

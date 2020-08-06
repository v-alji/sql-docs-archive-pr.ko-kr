---
title: MSSQLSERVER_7916 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7916 (Database Engine error)
ms.assetid: 9bac3536-de14-4e98-84c2-bde9a59ba0d1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 21b31eedf61369d9c4d1cfdfd5f53eebd3f5341c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651709"
---
# <a name="mssqlserver_7916"></a><span data-ttu-id="7f3e6-102">MSSQLSERVER_7916</span><span class="sxs-lookup"><span data-stu-id="7f3e6-102">MSSQLSERVER_7916</span></span>
    
## <a name="details"></a><span data-ttu-id="7f3e6-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="7f3e6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7f3e6-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="7f3e6-104">Product Name</span></span>|<span data-ttu-id="7f3e6-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="7f3e6-105">SQL Server</span></span>|  
|<span data-ttu-id="7f3e6-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="7f3e6-106">Event ID</span></span>|<span data-ttu-id="7f3e6-107">7916</span><span class="sxs-lookup"><span data-stu-id="7f3e6-107">7916</span></span>|  
|<span data-ttu-id="7f3e6-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="7f3e6-108">Event Source</span></span>|<span data-ttu-id="7f3e6-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7f3e6-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7f3e6-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="7f3e6-110">Component</span></span>|<span data-ttu-id="7f3e6-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="7f3e6-111">SQLEngine</span></span>|  
|<span data-ttu-id="7f3e6-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="7f3e6-112">Symbolic Name</span></span>|<span data-ttu-id="7f3e6-113">DBCC2_REPAIR_RECORD_DELETED</span><span class="sxs-lookup"><span data-stu-id="7f3e6-113">DBCC2_REPAIR_RECORD_DELETED</span></span>|  
|<span data-ttu-id="7f3e6-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="7f3e6-114">Message Text</span></span>|<span data-ttu-id="7f3e6-115">복구: 페이지 P_ID, 슬롯 S_ID에서 개체 ID O_ID, 인덱스 ID I_ID, 파티션 ID PN_ID, 할당 단위 ID A_ID(TYPE 유형)에 대한 레코드를 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="7f3e6-115">Repair: Deleted record for object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE), on page P_ID, slot S_ID.</span></span> <span data-ttu-id="7f3e6-116">인덱스를 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="7f3e6-116">Indexes will be rebuilt.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7f3e6-117">설명</span><span class="sxs-lookup"><span data-stu-id="7f3e6-117">Explanation</span></span>  
 <span data-ttu-id="7f3e6-118">지정된 레코드가 페이지에서 삭제되었음을 나타내는 REPAIR의 정보 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="7f3e6-118">This is an information messages from REPAIR that indicates the specified record was deleted from the page.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7f3e6-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="7f3e6-119">User Action</span></span>  
 <span data-ttu-id="7f3e6-120">None</span><span class="sxs-lookup"><span data-stu-id="7f3e6-120">None</span></span>  
  
  

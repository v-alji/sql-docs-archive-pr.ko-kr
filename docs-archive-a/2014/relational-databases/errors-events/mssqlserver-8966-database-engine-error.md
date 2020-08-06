---
title: MSSQLSERVER_8966 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8966 (Database Engine error)
ms.assetid: 6b1150fd-9dfd-4df9-8f08-8eca237667db
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8d3a12d5d0732ba8694db3d4c7dcae1eac59d28b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661669"
---
# <a name="mssqlserver_8966"></a><span data-ttu-id="70469-102">MSSQLSERVER_8966</span><span class="sxs-lookup"><span data-stu-id="70469-102">MSSQLSERVER_8966</span></span>
    
## <a name="details"></a><span data-ttu-id="70469-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="70469-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="70469-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="70469-104">Product Name</span></span>|<span data-ttu-id="70469-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="70469-105">SQL Server</span></span>|  
|<span data-ttu-id="70469-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="70469-106">Event ID</span></span>|<span data-ttu-id="70469-107">8966</span><span class="sxs-lookup"><span data-stu-id="70469-107">8966</span></span>|  
|<span data-ttu-id="70469-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="70469-108">Event Source</span></span>|<span data-ttu-id="70469-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="70469-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="70469-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="70469-110">Component</span></span>|<span data-ttu-id="70469-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="70469-111">SQLEngine</span></span>|  
|<span data-ttu-id="70469-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="70469-112">Symbolic Name</span></span>|<span data-ttu-id="70469-113">DBCC3_FAILED_TO_READ_AND_LATCH_PAGE</span><span class="sxs-lookup"><span data-stu-id="70469-113">DBCC3_FAILED_TO_READ_AND_LATCH_PAGE</span></span>|  
|<span data-ttu-id="70469-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="70469-114">Message Text</span></span>|<span data-ttu-id="70469-115">래치 유형이 TYPE인 페이지 P_ID을(를) 읽어 래치할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70469-115">Unable to read and latch page P_ID with latch type TYPE.</span></span> <span data-ttu-id="70469-116">OPERATION이(가) 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="70469-116">OPERATION failed.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="70469-117">설명</span><span class="sxs-lookup"><span data-stu-id="70469-117">Explanation</span></span>  
 <span data-ttu-id="70469-118">페이지를 읽지 못했거나 PFS 또는 GAM 페이지에서 래치를 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70469-118">The page read failed or a latch could not be taken on a PFS or GAM page.</span></span> <span data-ttu-id="70469-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그에 래치 제한 시간 또는 다른 관련 메시지가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70469-119">There may be latch time-out or other accompanying messages in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="70469-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="70469-120">User Action</span></span>  
 <span data-ttu-id="70469-121">SQL 오류 로그에서 관련 메시지를 살펴보고 오류를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="70469-121">Review the SQL error log for accompanying messages and resolve these errors.</span></span>  
  
  

---
title: MSSQLSERVER_3452 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3452 (Database Engine error)
ms.assetid: bf838f02-7186-4b33-b01e-361b0c02de1f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 662d342064e8094400a6b672e21704877b4d0448
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638810"
---
# <a name="mssqlserver_3452"></a><span data-ttu-id="cd420-102">MSSQLSERVER_3452</span><span class="sxs-lookup"><span data-stu-id="cd420-102">MSSQLSERVER_3452</span></span>
    
## <a name="details"></a><span data-ttu-id="cd420-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="cd420-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cd420-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="cd420-104">Product Name</span></span>|<span data-ttu-id="cd420-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="cd420-105">SQL Server</span></span>|  
|<span data-ttu-id="cd420-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="cd420-106">Event ID</span></span>|<span data-ttu-id="cd420-107">3452</span><span class="sxs-lookup"><span data-stu-id="cd420-107">3452</span></span>|  
|<span data-ttu-id="cd420-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="cd420-108">Event Source</span></span>|<span data-ttu-id="cd420-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="cd420-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="cd420-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="cd420-110">Component</span></span>|<span data-ttu-id="cd420-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="cd420-111">SQLEngine</span></span>|  
|<span data-ttu-id="cd420-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="cd420-112">Symbolic Name</span></span>|<span data-ttu-id="cd420-113">REC_CHECKIDENTITY</span><span class="sxs-lookup"><span data-stu-id="cd420-113">REC_CHECKIDENTITY</span></span>|  
|<span data-ttu-id="cd420-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="cd420-114">Message Text</span></span>|<span data-ttu-id="cd420-115">데이터베이스 '%.\*ls'(%d)을(를) 복구하는 동안 테이블 ID %d에서 ID 값이 일치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cd420-115">Recovery of database '%.\*ls' (%d) detected possible identity value inconsistency in table ID %d.</span></span> <span data-ttu-id="cd420-116">DBCC CHECKIDENT('%.\*ls')를 실행하세요.</span><span class="sxs-lookup"><span data-stu-id="cd420-116">Run DBCC CHECKIDENT ('%.\*ls').</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cd420-117">설명</span><span class="sxs-lookup"><span data-stu-id="cd420-117">Explanation</span></span>  
 <span data-ttu-id="cd420-118">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드하는 동안 데이터베이스의 ID 값을 복구하기 위한 프로세스에서 메타데이터의 불일치를 발견했습니다.</span><span class="sxs-lookup"><span data-stu-id="cd420-118">During the upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the process to recover the identity values in the database found an inconsistency in the metadata.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cd420-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="cd420-119">User Action</span></span>  
 <span data-ttu-id="cd420-120">DBCC CHECKIDENT를 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="cd420-120">Run DBCC CHECKIDENT.</span></span>  
  
  

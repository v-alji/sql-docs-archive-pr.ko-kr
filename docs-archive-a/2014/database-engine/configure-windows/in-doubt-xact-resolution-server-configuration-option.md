---
title: in-doubt xact resolution 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- distributed transactions [SQL Server], unresolved transactions
- unresolved transactions
- in-doubt xact resolution option
ms.assetid: 3426fd32-cad2-4f2f-8ca9-e0296cc12703
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6b8db57ef2a4ee85d65e8c25de28ff7ada7994e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729824"
---
# <a name="in-doubt-xact-resolution-server-configuration-option"></a><span data-ttu-id="116a7-102">in-doubt xact resolution 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="116a7-102">in-doubt xact resolution Server Configuration Option</span></span>
  <span data-ttu-id="116a7-103">**미결 트랜잭션 확인** 옵션을 사용하여 MS DTC( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator)가 해결할 수 없는 트랜잭션의 기본 결과를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="116a7-103">Use the **in-doubt xact resolution** option to control the default outcome of transactions that the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) is unable to resolve.</span></span> <span data-ttu-id="116a7-104">MS DTC가 꺼진 경우나 복구 시 알 수 없는 트랜잭션 결과가 있는 경우에는 트랜잭션을 해결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="116a7-104">Inability to resolve transactions may be related to the MS DTC down time or an unknown transaction outcome at the time of recovery.</span></span>  
  
 <span data-ttu-id="116a7-105">다음 표에서는 미결 트랜잭션을 해결하기 위한 가능한 결과 값 목록을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="116a7-105">The following table lists the possible outcome values for resolving an in-doubt transaction.</span></span>  
  
|<span data-ttu-id="116a7-106">결과 값</span><span class="sxs-lookup"><span data-stu-id="116a7-106">Outcome value</span></span>|<span data-ttu-id="116a7-107">Description</span><span class="sxs-lookup"><span data-stu-id="116a7-107">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="116a7-108">0</span><span class="sxs-lookup"><span data-stu-id="116a7-108">0</span></span>|<span data-ttu-id="116a7-109">가정 없음.</span><span class="sxs-lookup"><span data-stu-id="116a7-109">No presumption.</span></span> <span data-ttu-id="116a7-110">MS DTC가 미결 트랜잭션을 해결할 수 없으면 복구에 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="116a7-110">Recovery fails if MS DTC cannot resolve any in-doubt transactions.</span></span>|  
|<span data-ttu-id="116a7-111">1</span><span class="sxs-lookup"><span data-stu-id="116a7-111">1</span></span>|<span data-ttu-id="116a7-112">커밋 가정.</span><span class="sxs-lookup"><span data-stu-id="116a7-112">Presume commit.</span></span> <span data-ttu-id="116a7-113">모든 MS DTC 미결 트랜잭션을 커밋된 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="116a7-113">Any MS DTC in-doubt transactions are presumed to have committed.</span></span>|  
|<span data-ttu-id="116a7-114">2</span><span class="sxs-lookup"><span data-stu-id="116a7-114">2</span></span>|<span data-ttu-id="116a7-115">중단 가정.</span><span class="sxs-lookup"><span data-stu-id="116a7-115">Presume abort.</span></span> <span data-ttu-id="116a7-116">모든 MS DTC 미결 트랜잭션을 중단된 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="116a7-116">Any MS DTC in-doubt transactions are presumed to have aborted.</span></span>|  
  
 <span data-ttu-id="116a7-117">종료 시간이 연장되지 않게 하려면 관리자는 다음 예와 같이 이 옵션을 선택하여 커밋을 가정하거나 중단을 가정하도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="116a7-117">To minimize the possibility of extended down time, an administrator might choose to configure this option either to presume commit or presume abort, as shown in the following example.</span></span>  
  
```  
sp_configure 'show advanced options', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'in-doubt xact resolution', 2 -- presume abort  
GO  
RECONFIGURE  
GO  
sp_configure 'show advanced options', 0  
GO  
RECONFIGURE  
GO  
  
```  
  
 <span data-ttu-id="116a7-118">또한 관리자는 다음 예와 같이 기본값(가정 없음)을 유지하고 DTC 실패에 대해 알리기 위해 복구에 실패하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="116a7-118">Alternatively, the administrator might want to leave the default (no presumption) and allow recovery to fail in order to be made aware of a DTC failure, as shown in the following example.</span></span>  
  
```  
sp_configure 'show advanced options', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'in-doubt xact resolution', 1 -- presume commit  
GO  
reconfigure  
GO  
ALTER DATABASE pubs SET ONLINE -- run recovery again  
GO  
sp_configure 'in-doubt xact resolution', 0 -- back to no assumptions  
GO  
sp_configure 'show advanced options', 0  
GO  
RECONFIGURE  
GO  
  
```  
  
 <span data-ttu-id="116a7-119">**미결 트랜잭션 확인** 옵션은 고급 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="116a7-119">The **in-doubt xact resolution** option is an advanced option.</span></span> <span data-ttu-id="116a7-120">**sp_configure** 시스템 저장 프로시저를 사용하여 설정을 변경하는 경우 **고급 옵션 표시** 를 1로 설정할 때만 **미결 트랜잭션 확인** 을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="116a7-120">If you are using the **sp_configure** system stored procedure to change the setting, you can change **in-doubt xact resolution** only when **show advanced options** is set to 1.</span></span> <span data-ttu-id="116a7-121">이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="116a7-121">The setting takes effect immediately without a server restart.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="116a7-122">모든 분산 트랜잭션에 관련된 모든 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 이 옵션을 일관되게 구성하면 데이터 불일치를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="116a7-122">Consistent configuration of this option across all [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances involved in any distributed transactions will help avoid data inconsistencies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="116a7-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="116a7-123">See Also</span></span>  
 <span data-ttu-id="116a7-124">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="116a7-124">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="116a7-125">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="116a7-125">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="116a7-126">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="116a7-126">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  

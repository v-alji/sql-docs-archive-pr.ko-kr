---
title: disallow results from triggers 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- triggers [SQL Server], result sets
- result sets [SQL Server], triggers
- disallow results from triggers option
ms.assetid: 47149073-307d-47a5-b7d2-66a737d3231d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f162a6e06706561d861bfc54a1ae4027f2c3466e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727347"
---
# <a name="disallow-results-from-triggers-server-configuration-option"></a><span data-ttu-id="dd80f-102">disallow results from triggers 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="dd80f-102">disallow results from triggers Server Configuration Option</span></span>
  <span data-ttu-id="dd80f-103">**disallow results from triggers** 옵션을 사용하여 트리거에서 결과 집합을 반환하는지 여부를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd80f-103">Use the **disallow results from triggers** option to control whether triggers return result sets.</span></span> <span data-ttu-id="dd80f-104">결과 집합을 반환하는 트리거는 트리거가 작동하지 않는 애플리케이션에 예기치 않은 동작을 유발할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd80f-104">Triggers that return result sets may cause unexpected behavior in applications that are not designed to work with them.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] <span data-ttu-id="dd80f-105">이 값을 1로 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dd80f-105">We recommend that you set this value to 1.</span></span>  
  
 <span data-ttu-id="dd80f-106">1로 설정하면 **disallow results from triggers** 옵션이 ON으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd80f-106">When set to 1, the **disallow results from triggers** option is set to ON.</span></span> <span data-ttu-id="dd80f-107">이 옵션의 기본 설정은 0(OFF)입니다.</span><span class="sxs-lookup"><span data-stu-id="dd80f-107">The default setting for this option is 0 (OFF).</span></span> <span data-ttu-id="dd80f-108">이 옵션을 1(ON)로 설정하면 트리거가 결과 집합을 반환하지 못하며 사용자에게 다음 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd80f-108">If this option is set to 1 (ON), any attempt by a trigger to return a result set fails, and the user receives the following error message:</span></span>  
  
 <span data-ttu-id="dd80f-109">"Msg 524, 수준 16, 상태 1, 프로시저 \<Procedure Name>, 줄 \<Line#></span><span class="sxs-lookup"><span data-stu-id="dd80f-109">"Msg 524, Level 16, State 1, Procedure \<Procedure Name>, Line \<Line#></span></span>  
  
 <span data-ttu-id="dd80f-110">"트리거가 결과 집합을 반환했으며 서버 옵션 'disallow_results_from_triggers'가 True입니다."</span><span class="sxs-lookup"><span data-stu-id="dd80f-110">"A trigger returned a resultset and the server option 'disallow_results_from_triggers' is true."</span></span>  
  
 <span data-ttu-id="dd80f-111">**disallow results from triggers** 옵션은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 수준에서 적용되며, 인스턴스에 있는 기존의 모든 트리거에 대한 동작을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="dd80f-111">The **disallow results from triggers** option is applied at the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance level, and it will determine behavior for all existing triggers within the instance.</span></span>  
  
 <span data-ttu-id="dd80f-112">**disallow results from triggers** 옵션은 고급 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="dd80f-112">The **disallow results from triggers** option is an advanced option.</span></span> <span data-ttu-id="dd80f-113">**sp_configure** 시스템 저장 프로시저를 사용하여 설정을 변경하는 경우 **show advanced options** 를 1로 설정할 때만 disallow results from triggers를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd80f-113">If you are using the **sp_configure** system stored procedure to change the setting, you can change disallow results from triggers only when **show advanced options** is set to 1.</span></span> <span data-ttu-id="dd80f-114">이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd80f-114">The setting takes effect immediately without a server restart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd80f-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dd80f-115">See Also</span></span>  
 <span data-ttu-id="dd80f-116">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dd80f-116">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="dd80f-117">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="dd80f-117">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="dd80f-118">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dd80f-118">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  

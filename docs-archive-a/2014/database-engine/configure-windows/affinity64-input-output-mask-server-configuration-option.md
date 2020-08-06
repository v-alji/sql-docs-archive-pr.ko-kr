---
title: affinity64 I/O mask 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- processor affinity [SQL Server]
- binding processors [SQL Server]
- affinity64 I/O mask option
ms.assetid: d304eae7-5116-40ee-a0fa-0a3c0bc20c01
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 19616f5718254bde5601ea1beeec21412ad867de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652348"
---
# <a name="affinity64-input-output-mask-server-configuration-option"></a><span data-ttu-id="60198-102">affinity64 Input-Output mask 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="60198-102">affinity64 Input-Output mask Server Configuration Option</span></span>
  <span data-ttu-id="60198-103">**affinity64 I/O mask** 는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affinity I/O mask **옵션과 유사한 방식으로** 디스크 I/O를 지정한 CPU 하위 집합으로 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="60198-103">The **affinity64 I/O mask** binds [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disk I/O to a specified subset of CPUs, similar to the **affinity I/O mask** option.</span></span> <span data-ttu-id="60198-104">**affinity I/O mask** 를 사용하여 처음 32개의 프로세서를 바인딩한 다음 **affinity64 I/O mask** 를 사용하여 컴퓨터의 남은 프로세서를 바인딩하세요.</span><span class="sxs-lookup"><span data-stu-id="60198-104">Use **affinity I/O mask** to bind the first 32 processors, and use **affinity64 I/O mask** to bind the remaining processors on the computer.</span></span> <span data-ttu-id="60198-105">**affinity64 I/O mask**를 다시 구성하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="60198-105">If you reconfigure the **affinity64 I/O mask**, you must restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="60198-106">이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]64비트 버전에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60198-106">This option is only visible on the 64-bit version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60198-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="60198-107">See Also</span></span>  
 <span data-ttu-id="60198-108">[선호도 입력-출력 마스크 서버 구성 옵션](affinity-input-output-mask-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="60198-108">[affinity Input-Output mask Server Configuration Option](affinity-input-output-mask-server-configuration-option.md) </span></span>  
 <span data-ttu-id="60198-109">[리소스 사용 모니터링&#40;시스템 모니터&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="60198-109">[Monitor Resource Usage &#40;System Monitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md) </span></span>  
 <span data-ttu-id="60198-110">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="60198-110">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="60198-111">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="60198-111">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="60198-112">RECONFIGURE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="60198-112">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  

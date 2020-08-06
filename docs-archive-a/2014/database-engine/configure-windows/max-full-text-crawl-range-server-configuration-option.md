---
title: max full-text crawl range 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- crawls [full-text search]
- max full-text crawl range option
ms.assetid: a49de86b-0891-4dcd-89c0-ead30aab00e0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e1dbd9e44518b6e849a06a76e21fc605172fd2ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728688"
---
# <a name="max-full-text-crawl-range-server-configuration-option"></a><span data-ttu-id="fc29a-102">max full-text crawl range 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="fc29a-102">max full-text crawl range Server Configuration Option</span></span>
  <span data-ttu-id="fc29a-103">**max full-text crawl range** 옵션을 사용하여 CPU 사용률을 최적화함으로써 전체 탐색 중에 탐색 성능을 개선할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc29a-103">Use the **max full-text crawl range** option to optimize CPU utilization, which improves crawl performance during a full crawl.</span></span> <span data-ttu-id="fc29a-104">이 옵션을 사용하면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 전체 인덱스 탐색 중에 사용해야 하는 파티션의 수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc29a-104">Using this option, you can specify the number of partitions that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should use during a full index crawl.</span></span> <span data-ttu-id="fc29a-105">예를 들어 CPU가 여러 개 있고 사용률이 최적 상태가 아닌 경우 이 옵션의 최대값을 늘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc29a-105">For example, if there are many CPUs and their utilization is not optimal, you can increase the maximum value of this option.</span></span> <span data-ttu-id="fc29a-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 이 옵션 외에도 테이블의 행 수 및 CPU 수와 같은 여러 요소를 감안하여 실제 사용되는 파티션 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fc29a-106">In addition to this option, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses a number of other factors, such as the number of rows in the table and the number of CPUs, to determine the actual number of partitions used.</span></span>  
  
 <span data-ttu-id="fc29a-107">이 옵션의 기본값은 4이고 최소값은 1이며 최대값은 256입니다.</span><span class="sxs-lookup"><span data-stu-id="fc29a-107">The default value of this option is 4; the minimum value is 1, and the maximum value is 256.</span></span> <span data-ttu-id="fc29a-108">이 옵션을 변경하면 이후의 탐색에만 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="fc29a-108">Changes made to this option affect only subsequent crawls.</span></span> <span data-ttu-id="fc29a-109">실행 중인 탐색 작업은 변경된 옵션 설정의 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fc29a-109">Crawls in process will not be affected by a change in this option setting.</span></span>  
  
 <span data-ttu-id="fc29a-110">**max full-text crawl range** 옵션은 고급 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="fc29a-110">The **max full-text crawl range** option is an advanced option.</span></span> <span data-ttu-id="fc29a-111">**sp_configure** 시스템 저장 프로시저를 사용하여 설정을 변경하면 **show advanced options** 를 1로 설정할 때만 **max full-text crawl range** 를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc29a-111">If you are using the **sp_configure** system stored procedure to change the setting, you can change **max full-text crawl range** only when **show advanced options** is set to 1.</span></span> <span data-ttu-id="fc29a-112">이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc29a-112">The setting takes effect immediately without a server restart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc29a-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fc29a-113">See Also</span></span>  
 <span data-ttu-id="fc29a-114">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fc29a-114">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="fc29a-115">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fc29a-115">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="fc29a-116">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fc29a-116">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  

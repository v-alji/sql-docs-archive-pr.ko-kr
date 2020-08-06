---
title: ft crawl bandwidth 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- large memory buffers
- memory [SQL Server], buffers
- ft crawl bandwidth option
ms.assetid: e5864ad9-92f5-43b5-95de-46d68ded8694
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 33821ff1fdbc4248c71906d8307a8164a7f64d24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741239"
---
# <a name="ft-crawl-bandwidth-server-configuration-option"></a><span data-ttu-id="c0084-102">ft crawl bandwidth 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="c0084-102">ft crawl bandwidth Server Configuration Option</span></span>
  <span data-ttu-id="c0084-103">**ft crawl bandwidth** 옵션을 사용하여 대용량 메모리 버퍼 풀이 증가할 수 있는 크기를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0084-103">Use the **ft crawl bandwidth** option to specify the size to which the pool of large memory buffers can grow.</span></span> <span data-ttu-id="c0084-104">대용량 메모리 버퍼의 크기는 4MB입니다.</span><span class="sxs-lookup"><span data-stu-id="c0084-104">Large memory buffers are 4 megabytes (MB) in size.</span></span> <span data-ttu-id="c0084-105">**max** 매개 변수 값은 전체 텍스트 메모리 관리자가 대용량 버퍼 풀에서 유지 관리해야 하는 버퍼의 최대 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c0084-105">The **max** parameter value specifies the maximum number of buffers that the full-text memory manager should maintain in a large buffer pool.</span></span> <span data-ttu-id="c0084-106">**max** 값이 0이면 대용량 버퍼 풀에 가능한 버퍼 수에 제한이 없어집니다.</span><span class="sxs-lookup"><span data-stu-id="c0084-106">If the **max** value is zero, then there is no upper limit to the number of buffers that can be in a large buffer pool.</span></span>  
  
 <span data-ttu-id="c0084-107">**min** 매개 변수 값은 대용량 메모리 버퍼에서 유지 관리해야 하는 메모리 버퍼의 최소 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c0084-107">The **min** parameter specifies the minimum number of memory buffers that must be maintained in the pool of large memory buffers.</span></span> <span data-ttu-id="c0084-108">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 메모리 관리자의 요청이 있으면 모든 여분의 버퍼 풀이 해제되지만, 이 최소 버퍼 수는 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0084-108">Upon request from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory manager, all extra buffer pools will be released but this minimum number of buffers will be maintained.</span></span> <span data-ttu-id="c0084-109">하지만 지정된 **min** 값이 0일 경우 모든 메모리 버퍼가 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0084-109">If, however, the **min** value specified is zero, then all memory buffers are released.</span></span>  
  
 <span data-ttu-id="c0084-110">특정 환경에서는 현재 할당된 버퍼 수가 **min** 매개 변수에 지정된 값보다 작을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0084-110">Under certain circumstances, the number of buffers currently allocated is less than the value specified by the **min** parameter.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c0084-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c0084-111">See Also</span></span>  
 <span data-ttu-id="c0084-112">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c0084-112">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="c0084-113">[ft notify bandwidth 서버 구성 옵션](ft-notify-bandwidth-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="c0084-113">[ft notify bandwidth Server Configuration Option](ft-notify-bandwidth-server-configuration-option.md) </span></span>  
 [<span data-ttu-id="c0084-114">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c0084-114">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  

---
title: ft notify bandwidth 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- ft notify bandwidth opion
- small memory buffers
- memory [SQL Server], buffers
ms.assetid: 9ca284c5-f3e0-4a67-a132-fff376ff0ffe
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dc5839f699d55edf86c5e3e3f0eb001089a0a5dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738757"
---
# <a name="ft-notify-bandwidth-server-configuration-option"></a><span data-ttu-id="981dc-102">ft notify bandwidth 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="981dc-102">ft notify bandwidth Server Configuration Option</span></span>
  <span data-ttu-id="981dc-103">**ft notify bandwidth** 옵션을 사용하여 작은 메모리 버퍼의 풀이 증가할 수 있는 최대 크기를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="981dc-103">Use the **ft notify bandwidth** option to specify the size to which the pool of small memory buffers can grow.</span></span> <span data-ttu-id="981dc-104">작은 메모리 버퍼의 크기는 64KB입니다.</span><span class="sxs-lookup"><span data-stu-id="981dc-104">Small memory buffers are 64 kilobytes (KB) in size.</span></span> <span data-ttu-id="981dc-105">매개 변수 값은 전체 텍스트 메모리 관리자가 작은 버퍼 풀에서 유지해야 하는 *최대* 버퍼 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="981dc-105">The *max* parameter value specifies the maximum number of buffers that the full-text memory manager should maintain in a small buffer pool.</span></span> <span data-ttu-id="981dc-106">`max`값이 0 인 경우 작은 버퍼 풀에 있을 수 있는 버퍼 수에 대 한 상한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="981dc-106">If the `max` value is zero, then there is no upper limit to the number of buffers that can be in a small buffer pool.</span></span>  
  
 <span data-ttu-id="981dc-107">**min** 매개 변수는 작은 메모리 버퍼의 풀에서 유지되어야 하는 최소 메모리 버퍼 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="981dc-107">The **min** parameter specifies the minimum number of memory buffers that must be maintained in the pool of small memory buffers.</span></span> <span data-ttu-id="981dc-108">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 메모리 관리자의 요청이 있으면 모든 여분의 버퍼 풀이 해제되지만, 이 최소 버퍼 수는 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="981dc-108">Upon request from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory manager, all extra buffer pools will be released but this minimum number of buffers will be maintained.</span></span> <span data-ttu-id="981dc-109">하지만 지정된 **min** 값이 0일 경우 모든 메모리 버퍼가 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="981dc-109">If, however, the **min** value specified is zero, then all memory buffers are released.</span></span>  
  
 <span data-ttu-id="981dc-110">경우에 따라 현재 할당된 버퍼 수가 **min** 매개 변수에 지정된 값보다 낮을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="981dc-110">Under certain circumstances the number of buffers currently allocated is less than the value specified by the **min** parameter.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="981dc-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="981dc-111">See Also</span></span>  
 <span data-ttu-id="981dc-112">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="981dc-112">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="981dc-113">[ft crawl bandwidth 서버 구성 옵션](ft-crawl-bandwidth-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="981dc-113">[ft crawl bandwidth Server Configuration Option](ft-crawl-bandwidth-server-configuration-option.md) </span></span>  
 [<span data-ttu-id="981dc-114">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="981dc-114">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  

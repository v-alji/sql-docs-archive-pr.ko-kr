---
title: PH timeout 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- time limit for protocol handler wait [SQL Server]
- timeout options [SQL Server], ph timeout option
- protocols [SQL Server], timing out
- ph timeout option
ms.assetid: ed19a07c-83fe-4582-9c9e-41b1ce571850
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 515ed74a4b92259d53770bf6d970626eba686453
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729799"
---
# <a name="ph-timeout-server-configuration-option"></a><span data-ttu-id="3b4c6-102">PH timeout 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="3b4c6-102">PH timeout Server Configuration Option</span></span>
  <span data-ttu-id="3b4c6-103">PH timeout 옵션을 사용하여 전체 텍스트 프로토콜 처리기가 제한 시간까지 데이터베이스에 대한 연결을 대기하는 시간(초)을 지정할 수 있습니다. 기본값은 60초입니다.</span><span class="sxs-lookup"><span data-stu-id="3b4c6-103">Use the PH timeout option to specify the time, in seconds, that the full-text protocol handler should wait to connect to a database before timing out. The default value is 60 seconds.</span></span> <span data-ttu-id="3b4c6-104">일시적인 네트워크 문제로 인해 연결 시간을 초과하는 경우 ph timeout 값을 늘리십시오.</span><span class="sxs-lookup"><span data-stu-id="3b4c6-104">Increase the ph timeout value when connection attempts are timing out due to temporary network issues.</span></span>  
  
 <span data-ttu-id="3b4c6-105">전체 텍스트 프로토콜 처리기는 필터 데몬 호스트에 호스팅되며 SQL Server에서 전체 텍스트 인덱싱할 데이터를 인출하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b4c6-105">The full-text protocol handler is hosted in the filter daemon host and is used to fetch from SQL Server the data to be full-text indexed.</span></span> <span data-ttu-id="3b4c6-106">전체 텍스트 검색 구성 요소에 대한 자세한 내용은 [전체 텍스트 검색](../../relational-databases/search/full-text-search.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b4c6-106">For more information about full-text search components, see [Full-Text Search](../../relational-databases/search/full-text-search.md).</span></span>  
  
 <span data-ttu-id="3b4c6-107">데이터 행을 인출할 때 프로토콜 처리기에서 지정한 시간 내에 SQL Server에 연결할 수 없으면 해당 행에 대한 제한 시간 오류를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="3b4c6-107">When attempting to fetch a data row, if the protocol handler cannot connect to SQL Server within the specified time, it reports a time-out error for that row.</span></span> <span data-ttu-id="3b4c6-108">전체 텍스트 Gatherer는 나중에 행을 다시 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="3b4c6-108">The full-text gatherer will retry the row later.</span></span> <span data-ttu-id="3b4c6-109">전체 텍스트 Gatherer에 대한 자세한 내용은 [전체 텍스트 인덱스 채우기](../../relational-databases/indexes/indexes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b4c6-109">For more information about the full-text gatherer, see [Populate Full-Text Indexes](../../relational-databases/indexes/indexes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b4c6-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3b4c6-110">See Also</span></span>  
 <span data-ttu-id="3b4c6-111">[전체 텍스트 검색](../../relational-databases/search/full-text-search.md) </span><span class="sxs-lookup"><span data-stu-id="3b4c6-111">[Full-Text Search](../../relational-databases/search/full-text-search.md) </span></span>  
 <span data-ttu-id="3b4c6-112">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3b4c6-112">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="3b4c6-113">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3b4c6-113">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="3b4c6-114">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3b4c6-114">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  

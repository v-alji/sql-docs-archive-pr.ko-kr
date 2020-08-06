---
title: MSSQLSERVER_7308 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7308 (Database Engine error)
- single-threaded apartment mode
ms.assetid: cca9eab9-afb9-463d-abfd-0802257e2c99
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9978f35ebe41eeda1470220772f87e83ab1ad942
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651013"
---
# <a name="mssqlserver_7308"></a><span data-ttu-id="03d7a-102">MSSQLSERVER_7308</span><span class="sxs-lookup"><span data-stu-id="03d7a-102">MSSQLSERVER_7308</span></span>
    
## <a name="details"></a><span data-ttu-id="03d7a-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="03d7a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="03d7a-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="03d7a-104">Product Name</span></span>|<span data-ttu-id="03d7a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="03d7a-105">SQL Server</span></span>|  
|<span data-ttu-id="03d7a-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="03d7a-106">Event ID</span></span>|<span data-ttu-id="03d7a-107">7308</span><span class="sxs-lookup"><span data-stu-id="03d7a-107">7308</span></span>|  
|<span data-ttu-id="03d7a-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="03d7a-108">Event Source</span></span>|<span data-ttu-id="03d7a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="03d7a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="03d7a-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="03d7a-110">Component</span></span>|<span data-ttu-id="03d7a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="03d7a-111">SQLEngine</span></span>|  
|<span data-ttu-id="03d7a-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="03d7a-112">Symbolic Name</span></span>|<span data-ttu-id="03d7a-113">RMT_STA_DISABLED</span><span class="sxs-lookup"><span data-stu-id="03d7a-113">RMT_STA_DISABLED</span></span>|  
|<span data-ttu-id="03d7a-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="03d7a-114">Message Text</span></span>|<span data-ttu-id="03d7a-115">OLE DB 공급자 '%ls'은(는) 단일 스레드 아파트 모드에서 실행되도록 구성되어 있으므로 분산 쿼리에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="03d7a-115">OLE DB provider '%ls' cannot be used for distributed queries because the provider is configured to run in single-threaded apartment mode.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="03d7a-116">설명</span><span class="sxs-lookup"><span data-stu-id="03d7a-116">Explanation</span></span>  
 <span data-ttu-id="03d7a-117">STA(단일 스레드 아파트) 모드에서 실행되도록 구성된 OLE DB 공급자를 사용했습니다.</span><span class="sxs-lookup"><span data-stu-id="03d7a-117">You have used an OLE DB provider that is configured to run in single-threaded apartment (STA) mode.</span></span> <span data-ttu-id="03d7a-118">STA(단일 스레드 아파트) 모드에서 실행되도록 구성된 OLE DB 공급자는 분산 쿼리에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="03d7a-118">OLE DB providers that run in single-threaded apartment (STA) mode cannot be used for distributed queries.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="03d7a-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="03d7a-119">User Action</span></span>  
 <span data-ttu-id="03d7a-120">이 문제를 해결하려면 MTA(다중 스레드 아파트) 모드에서 실행되도록 OLE DB 공급자를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="03d7a-120">To resolve this error, configure the provider to run in multithreaded apartment (MTA) mode.</span></span> <span data-ttu-id="03d7a-121">OLE DB 공급자가 MTA를 지원하지 않으며 MTA를 지원하는 버전으로 OLE DB 공급자를 업그레이드할 수 없는 경우 out-of-process를 실행하도록 OLE DB 공급자를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="03d7a-121">If the provider does not support MTA, and the provider cannot be upgraded to a version that supports MTA, consider configuring the provider to run out-of-process.</span></span> <span data-ttu-id="03d7a-122">OLE DB 공급자가 MTA 또는 out-of-process 실행을 지원하는 경우 해당 OLE DB 공급자의 공급업체는 사용자에게 이를 알려줄 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03d7a-122">The provider vendor should be able to tell you if the provider supports MTA or running out-of-process.</span></span>  
  
  

---
title: MSSQLSERVER_9692 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9692 (Database Engine error)
ms.assetid: 02399d6e-ab5e-4f30-8a3e-2bb1e8c135b5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6b6ba95771aafffa5a322ffa1b7443419936addd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650031"
---
# <a name="mssqlserver_9692"></a><span data-ttu-id="f1d47-102">MSSQLSERVER_9692</span><span class="sxs-lookup"><span data-stu-id="f1d47-102">MSSQLSERVER_9692</span></span>
    
## <a name="details"></a><span data-ttu-id="f1d47-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="f1d47-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f1d47-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="f1d47-104">Product Name</span></span>|<span data-ttu-id="f1d47-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f1d47-105">SQL Server</span></span>|  
|<span data-ttu-id="f1d47-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="f1d47-106">Event ID</span></span>|<span data-ttu-id="f1d47-107">9692</span><span class="sxs-lookup"><span data-stu-id="f1d47-107">9692</span></span>|  
|<span data-ttu-id="f1d47-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="f1d47-108">Event Source</span></span>|<span data-ttu-id="f1d47-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f1d47-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f1d47-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="f1d47-110">Component</span></span>|<span data-ttu-id="f1d47-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f1d47-111">SQLEngine</span></span>|  
|<span data-ttu-id="f1d47-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="f1d47-112">Symbolic Name</span></span>|<span data-ttu-id="f1d47-113">SB2_CANT_LISTEN_PORT_IN_USE</span><span class="sxs-lookup"><span data-stu-id="f1d47-113">SB2_CANT_LISTEN_PORT_IN_USE</span></span>|  
|<span data-ttu-id="f1d47-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="f1d47-114">Message Text</span></span>|<span data-ttu-id="f1d47-115">다른 프로세스에 사용 중이므로 %S_MSG 프로토콜 전송이 포트 %d에서 수신할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f1d47-115">The %S_MSG protocol transport cannot listen on port %d because it is in use by another process.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f1d47-116">설명</span><span class="sxs-lookup"><span data-stu-id="f1d47-116">Explanation</span></span>  
 <span data-ttu-id="f1d47-117">지정된 TCP 포트를 컴퓨터의 다른 프로그램에서 사용 중입니다.</span><span class="sxs-lookup"><span data-stu-id="f1d47-117">Another program on the computer is using the TCP port indicated.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f1d47-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="f1d47-118">User Action</span></span>  
 <span data-ttu-id="f1d47-119">`netstat -aon`를 실행 하 여 포트를 사용 중인 프로그램을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d47-119">Run `netstat -aon` to determine what program is using the port.</span></span> <span data-ttu-id="f1d47-120">해당 애플리케이션을 비활성화하거나 Service Broker에 다른 포트를 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="f1d47-120">Disable that application or specify a different port for Service Broker.</span></span>  
  
  

---
title: MSSQLSERVER_10061 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "10061"
helpviewer_keywords:
- 10061 (Database Engine error)
ms.assetid: 729602f3-08df-474c-8740-8dea13c1eee3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0c866bd8dce01f65036f1d508a94252a97613424
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735280"
---
# <a name="mssqlserver_10061"></a><span data-ttu-id="972ac-102">MSSQLSERVER_10061</span><span class="sxs-lookup"><span data-stu-id="972ac-102">MSSQLSERVER_10061</span></span>
    
## <a name="details"></a><span data-ttu-id="972ac-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="972ac-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="972ac-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="972ac-104">Product Name</span></span>|<span data-ttu-id="972ac-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="972ac-105">SQL Server</span></span>|  
|<span data-ttu-id="972ac-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="972ac-106">Event ID</span></span>|<span data-ttu-id="972ac-107">10061</span><span class="sxs-lookup"><span data-stu-id="972ac-107">10061</span></span>|  
|<span data-ttu-id="972ac-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="972ac-108">Event Source</span></span>|<span data-ttu-id="972ac-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="972ac-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="972ac-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="972ac-110">Component</span></span>|<span data-ttu-id="972ac-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="972ac-111">SQLEngine</span></span>|  
|<span data-ttu-id="972ac-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="972ac-112">Symbolic Name</span></span>||  
|<span data-ttu-id="972ac-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="972ac-113">Message Text</span></span>|<span data-ttu-id="972ac-114">서버에 대한 연결을 구성하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="972ac-114">An error has occurred while establishing a connection to the server.</span></span>  <span data-ttu-id="972ac-115">SQL Server에 연결할 때 기본 설정에서 SQL Server가 원격 연결을 허용하지 않기 때문에 이 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="972ac-115">When connecting to SQL Server, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections.</span></span> <span data-ttu-id="972ac-116">(공급자: TCP 공급자, 오류: 0 - 대상 머신에서 연결을 거부했으므로 연결하지 못했습니다.) (Microsoft SQL Server, 오류: 10061)</span><span class="sxs-lookup"><span data-stu-id="972ac-116">(provider: TCP Provider, error: 0 - No connection could be made because the target machine actively refused it.) (Microsoft SQL Server, Error: 10061)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="972ac-117">설명</span><span class="sxs-lookup"><span data-stu-id="972ac-117">Explanation</span></span>  
 <span data-ttu-id="972ac-118">서버가 클라이언트 요청에 응답하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="972ac-118">The server did not respond to the client request.</span></span> <span data-ttu-id="972ac-119">서버가 시작되지 않았기 때문에 이 오류가 발생했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="972ac-119">This error could occur because the server is not started.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="972ac-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="972ac-120">User Action</span></span>  
 <span data-ttu-id="972ac-121">서버가 시작되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="972ac-121">Make sure that the server is started.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="972ac-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="972ac-122">See Also</span></span>  
 <span data-ttu-id="972ac-123">[데이터베이스 엔진 서비스 관리](../../database-engine/configure-windows/manage-the-database-engine-services.md) </span><span class="sxs-lookup"><span data-stu-id="972ac-123">[Manage the Database Engine Services](../../database-engine/configure-windows/manage-the-database-engine-services.md) </span></span>  
 <span data-ttu-id="972ac-124">[클라이언트 프로토콜 구성](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="972ac-124">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 <span data-ttu-id="972ac-125">[네트워크 프로토콜 및 네트워크 라이브러리](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="972ac-125">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="972ac-126">[클라이언트 네트워크 구성](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="972ac-126">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="972ac-127">[클라이언트 프로토콜 구성](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="972ac-127">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="972ac-128">서버 네트워크 프로토콜 설정 또는 해제</span><span class="sxs-lookup"><span data-stu-id="972ac-128">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  

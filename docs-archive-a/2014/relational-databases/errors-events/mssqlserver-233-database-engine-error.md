---
title: MSSQLSERVER_233 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "233"
helpviewer_keywords:
- 233 (Database Engine error)
ms.assetid: 201665dc-7ac8-4c19-90d3-33354c5caa72
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8c51fac7c0af16c520d7cf5538e512912e62cf87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730711"
---
# <a name="mssqlserver_233"></a><span data-ttu-id="53864-102">MSSQLSERVER_233</span><span class="sxs-lookup"><span data-stu-id="53864-102">MSSQLSERVER_233</span></span>
    
## <a name="details"></a><span data-ttu-id="53864-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="53864-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="53864-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="53864-104">Product Name</span></span>|<span data-ttu-id="53864-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="53864-105">SQL Server</span></span>|  
|<span data-ttu-id="53864-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="53864-106">Event ID</span></span>|<span data-ttu-id="53864-107">233</span><span class="sxs-lookup"><span data-stu-id="53864-107">233</span></span>|  
|<span data-ttu-id="53864-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="53864-108">Event Source</span></span>|<span data-ttu-id="53864-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="53864-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="53864-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="53864-110">Component</span></span>|<span data-ttu-id="53864-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="53864-111">SQLEngine</span></span>|  
|<span data-ttu-id="53864-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="53864-112">Symbolic Name</span></span>||  
|<span data-ttu-id="53864-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="53864-113">Message Text</span></span>|<span data-ttu-id="53864-114">서버에 성공적으로 연결되었지만 로그인 중 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="53864-114">A connection was successfully established with the server, but then an error occurred during the login process.</span></span> <span data-ttu-id="53864-115">(공급자: 공유 메모리 공급자, 오류: 0 - 파이프의 한쪽 끝에 프로세스가 없습니다.) (Microsoft SQL Server, 오류: 233)</span><span class="sxs-lookup"><span data-stu-id="53864-115">(provider: Shared Memory Provider, error: 0 - No process is on the other end of the pipe.) (Microsoft SQL Server, Error: 233)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="53864-116">설명</span><span class="sxs-lookup"><span data-stu-id="53864-116">Explanation</span></span>  
 <span data-ttu-id="53864-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 클라이언트가 서버에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="53864-117">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client cannot connect to the server.</span></span> <span data-ttu-id="53864-118">서버가 원격 연결을 허용하도록 구성되어 있지 않기 때문에 이 오류가 발생했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53864-118">This error could occur because the server is not configured to accept remote connections.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="53864-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="53864-119">User Action</span></span>  
 <span data-ttu-id="53864-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자 도구를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 원격 연결을 허용하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="53864-120">Use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager tool to allow [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to accept remote connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53864-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="53864-121">See Also</span></span>  
 <span data-ttu-id="53864-122">[네트워크 프로토콜 및 네트워크 라이브러리](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="53864-122">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="53864-123">[클라이언트 네트워크 구성](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="53864-123">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="53864-124">[클라이언트 프로토콜 구성](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="53864-124">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="53864-125">서버 네트워크 프로토콜 설정 또는 해제</span><span class="sxs-lookup"><span data-stu-id="53864-125">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  

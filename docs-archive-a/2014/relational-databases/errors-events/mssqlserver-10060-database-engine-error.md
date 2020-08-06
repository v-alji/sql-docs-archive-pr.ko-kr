---
title: MSSQLSERVER_10060 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "10060"
helpviewer_keywords:
- 10060 (Database Engine error)
ms.assetid: 28c21277-cad8-406c-a955-07933a56982a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d634cfb06381fb916ef2e421e0677e76edb9ae02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738452"
---
# <a name="mssqlserver_10060"></a><span data-ttu-id="84a7e-102">MSSQLSERVER_10060</span><span class="sxs-lookup"><span data-stu-id="84a7e-102">MSSQLSERVER_10060</span></span>
    
## <a name="details"></a><span data-ttu-id="84a7e-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="84a7e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="84a7e-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="84a7e-104">Product Name</span></span>|<span data-ttu-id="84a7e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="84a7e-105">SQL Server</span></span>|  
|<span data-ttu-id="84a7e-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="84a7e-106">Event ID</span></span>|<span data-ttu-id="84a7e-107">10060</span><span class="sxs-lookup"><span data-stu-id="84a7e-107">10060</span></span>|  
|<span data-ttu-id="84a7e-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="84a7e-108">Event Source</span></span>|<span data-ttu-id="84a7e-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="84a7e-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="84a7e-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="84a7e-110">Component</span></span>|<span data-ttu-id="84a7e-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="84a7e-111">SQLEngine</span></span>|  
|<span data-ttu-id="84a7e-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="84a7e-112">Symbolic Name</span></span>||  
|<span data-ttu-id="84a7e-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="84a7e-113">Message Text</span></span>|<span data-ttu-id="84a7e-114">서버에 대한 연결을 구성하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="84a7e-114">An error has occurred while establishing a connection to the server.</span></span>  <span data-ttu-id="84a7e-115">SQL Server에 연결할 때 기본 설정에서 SQL Server가 원격 연결을 허용하지 않기 때문에 이 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84a7e-115">When connecting to SQL Server, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections.</span></span> <span data-ttu-id="84a7e-116">(공급자: TCP 공급자, 오류: 0 - 연결된 구성원으로부터 응답이 없어 연결하지 못했거나, 호스트로부터 응답이 없어 연결이 끊어졌습니다.) (Microsoft SQL Server, 오류: 10060)</span><span class="sxs-lookup"><span data-stu-id="84a7e-116">(provider: TCP Provider, error: 0 - A connection attempt failed because the connected party did not properly respond after a period of time, or established connection failed because connected host has failed to respond.) (Microsoft SQL Server, Error: 10060)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="84a7e-117">설명</span><span class="sxs-lookup"><span data-stu-id="84a7e-117">Explanation</span></span>  
 <span data-ttu-id="84a7e-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 클라이언트가 서버에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="84a7e-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client cannot connect to the server.</span></span> <span data-ttu-id="84a7e-119">이 오류는 서버의 방화벽으로 인해 연결이 거부되었거나 서버가 원격 연결을 허용하도록 구성되어 있지 않아 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84a7e-119">This error could occur because either the firewall on the server has refused the connection or the server is not configured to accept remote connections.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="84a7e-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="84a7e-120">User Action</span></span>  
 <span data-ttu-id="84a7e-121">이 오류를 해결하려면 다음 동작 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="84a7e-121">To resolve this error, try one of the following actions:</span></span>  
  
-   <span data-ttu-id="84a7e-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 이 인스턴스가 연결을 허용하도록 컴퓨터의 방화벽을 구성했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="84a7e-122">Make sure that you have configured the firewall on the computer to allow this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to accept connections.</span></span>  
  
-   <span data-ttu-id="84a7e-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자 도구를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 원격 연결을 허용하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="84a7e-123">Use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager tool to allow [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to accept remote connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84a7e-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="84a7e-124">See Also</span></span>  
 <span data-ttu-id="84a7e-125">[데이터베이스 엔진 액세스에 대 한 Windows 방화벽 구성](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) </span><span class="sxs-lookup"><span data-stu-id="84a7e-125">[Configure a Windows Firewall for Database Engine Access](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) </span></span>  
 <span data-ttu-id="84a7e-126">[클라이언트 프로토콜 구성](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="84a7e-126">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 <span data-ttu-id="84a7e-127">[네트워크 프로토콜 및 네트워크 라이브러리](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="84a7e-127">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="84a7e-128">[클라이언트 네트워크 구성](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="84a7e-128">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="84a7e-129">[클라이언트 프로토콜 구성](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="84a7e-129">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="84a7e-130">서버 네트워크 프로토콜 설정 또는 해제</span><span class="sxs-lookup"><span data-stu-id="84a7e-130">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  

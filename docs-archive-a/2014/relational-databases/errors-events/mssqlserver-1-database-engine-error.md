---
title: MSSQLSERVER_-1 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "-1"
helpviewer_keywords:
- -1 (Database Engine error)
ms.assetid: bad25b91-eaed-46c0-a5b7-71117a32304c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 880212b1d2e9572bbb31535a5ba68b445c7e6f35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735287"
---
# <a name="mssqlserver_-1"></a><span data-ttu-id="3aacc-102">MSSQLSERVER_-1</span><span class="sxs-lookup"><span data-stu-id="3aacc-102">MSSQLSERVER_-1</span></span>
    
## <a name="details"></a><span data-ttu-id="3aacc-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="3aacc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3aacc-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="3aacc-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="3aacc-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="3aacc-105">Event ID</span></span>|<span data-ttu-id="3aacc-106">-1</span><span class="sxs-lookup"><span data-stu-id="3aacc-106">-1</span></span>|  
|<span data-ttu-id="3aacc-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="3aacc-107">Event Source</span></span>|<span data-ttu-id="3aacc-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="3aacc-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="3aacc-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="3aacc-109">Component</span></span>|<span data-ttu-id="3aacc-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="3aacc-110">SQLEngine</span></span>|  
|<span data-ttu-id="3aacc-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="3aacc-111">Symbolic Name</span></span>||  
|<span data-ttu-id="3aacc-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="3aacc-112">Message Text</span></span>|<span data-ttu-id="3aacc-113">서버에 대한 연결을 구성하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="3aacc-113">An error has occurred while establishing a connection to the server.</span></span>  <span data-ttu-id="3aacc-114">기본 설정 시 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 원격 연결이 허용되지 않기 때문에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 연결할 때 이 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3aacc-114">When connecting to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this failure may be caused by the fact that under the default settings [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not allow remote connections.</span></span> <span data-ttu-id="3aacc-115">(공급자: SQL 네트워크 인터페이스, 오류: 28 - 서버가 요청한 프로토콜을 지원하지 않습니다.) (Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], 오류: -1)</span><span class="sxs-lookup"><span data-stu-id="3aacc-115">(provider: SQL Network Interfaces, error: 28 - Server doesn't support requested protocol) (Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Error: -1)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3aacc-116">설명</span><span class="sxs-lookup"><span data-stu-id="3aacc-116">Explanation</span></span>  
 <span data-ttu-id="3aacc-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 클라이언트가 서버에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3aacc-117">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client cannot connect to the server.</span></span> <span data-ttu-id="3aacc-118">이 오류는 다음과 같은 이유로 인해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3aacc-118">This error could be caused by one of the following reasons:</span></span>  
  
-   <span data-ttu-id="3aacc-119">지정한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 이름이 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3aacc-119">A specified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance name is not valid.</span></span>  
  
-   <span data-ttu-id="3aacc-120">TCP, 즉 명명된 파이프 프로토콜이 활성화되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3aacc-120">The TCP, or named pipes protocols are not enabled.</span></span>  
  
-   <span data-ttu-id="3aacc-121">서버의 방화벽에서 연결을 거부했습니다.</span><span class="sxs-lookup"><span data-stu-id="3aacc-121">The firewall on the server has refused the connection.</span></span>  
  
-   <span data-ttu-id="3aacc-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 서비스(sqlbrowser)가 시작되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="3aacc-122">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service (sqlbrowser) is not started.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3aacc-123">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="3aacc-123">User Action</span></span>  
 <span data-ttu-id="3aacc-124">이 오류를 해결하려면 다음 동작 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3aacc-124">To resolve this error, try one of the following actions:</span></span>  
  
-   <span data-ttu-id="3aacc-125">연결 문자열에 지정된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 이름의 철자를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3aacc-125">Check the spelling of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance name that is specified in the connection string.</span></span>  
  
-   <span data-ttu-id="3aacc-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자 도구를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 TCP 또는 명명된 파이프 프로토콜을 통한 원격 연결을 허용하도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3aacc-126">Use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager tool to enable [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to accept remote connections over the TCP or named pipes protocols.</span></span>  
  
-   <span data-ttu-id="3aacc-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 서버 인스턴스에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 대한 포트 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 포트(UDP 1434)를 열도록 방화벽을 구성했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3aacc-127">Make sure that you have configured the firewall on the server instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to open ports for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser port (UDP 1434).</span></span>  
  
-   <span data-ttu-id="3aacc-128">서버에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 서비스가 시작되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3aacc-128">Make sure that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service is started on the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aacc-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3aacc-129">See Also</span></span>  
 <span data-ttu-id="3aacc-130">[데이터베이스 엔진 액세스에 대 한 Windows 방화벽 구성](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) </span><span class="sxs-lookup"><span data-stu-id="3aacc-130">[Configure a Windows Firewall for Database Engine Access](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) </span></span>  
 <span data-ttu-id="3aacc-131">[클라이언트 프로토콜 구성](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="3aacc-131">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 <span data-ttu-id="3aacc-132">[네트워크 프로토콜 및 네트워크 라이브러리](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="3aacc-132">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="3aacc-133">[클라이언트 네트워크 구성](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="3aacc-133">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="3aacc-134">[클라이언트 프로토콜 구성](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="3aacc-134">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="3aacc-135">서버 네트워크 프로토콜 설정 또는 해제</span><span class="sxs-lookup"><span data-stu-id="3aacc-135">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  

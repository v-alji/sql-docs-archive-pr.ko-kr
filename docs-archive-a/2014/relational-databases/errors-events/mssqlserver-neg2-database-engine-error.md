---
title: MSSQLSERVER_-2 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "2"
helpviewer_keywords:
- -2 (Database Engine error)
ms.assetid: f37a7b7d-26e1-4b9e-bcb4-57f7805393d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5d39b4a11387a60056bba3f87adffcb2653b60f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732688"
---
# <a name="mssqlserver_-2"></a><span data-ttu-id="53f39-102">MSSQLSERVER_-2</span><span class="sxs-lookup"><span data-stu-id="53f39-102">MSSQLSERVER_-2</span></span>
    
## <a name="details"></a><span data-ttu-id="53f39-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="53f39-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="53f39-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="53f39-104">Product Name</span></span>|<span data-ttu-id="53f39-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="53f39-105">SQL Server</span></span>|  
|<span data-ttu-id="53f39-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="53f39-106">Event ID</span></span>|<span data-ttu-id="53f39-107">-2</span><span class="sxs-lookup"><span data-stu-id="53f39-107">-2</span></span>|  
|<span data-ttu-id="53f39-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="53f39-108">Event Source</span></span>|<span data-ttu-id="53f39-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="53f39-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="53f39-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="53f39-110">Component</span></span>|<span data-ttu-id="53f39-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="53f39-111">SQLEngine</span></span>|  
|<span data-ttu-id="53f39-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="53f39-112">Symbolic Name</span></span>||  
|<span data-ttu-id="53f39-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="53f39-113">Message Text</span></span>|<span data-ttu-id="53f39-114">제한 시간이 만료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="53f39-114">Timeout expired.</span></span>  <span data-ttu-id="53f39-115">작업이 완료되기 전에 제한 시간이 초과되었거나 서버가 응답하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="53f39-115">The timeout period elapsed prior to completion of the operation or the server is not responding.</span></span> <span data-ttu-id="53f39-116">(Microsoft SQL Server, 오류: -2)</span><span class="sxs-lookup"><span data-stu-id="53f39-116">(Microsoft SQL Server, Error: -2)</span></span>|   
  
## <a name="explanation"></a><span data-ttu-id="53f39-117">설명</span><span class="sxs-lookup"><span data-stu-id="53f39-117">Explanation</span></span>  
 <span data-ttu-id="53f39-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 클라이언트가 서버에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="53f39-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client cannot connect to the server.</span></span> <span data-ttu-id="53f39-119">서버의 방화벽에서 연결을 거부했기 때문에 이 오류가 발생했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53f39-119">This error could occur because the firewall on the server has refused the connection.</span></span> 
  
## <a name="user-action"></a><span data-ttu-id="53f39-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="53f39-120">User Action</span></span>  
 <span data-ttu-id="53f39-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 서버 인스턴스에 있는 방화벽이 연결을 허용하도록 구성되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="53f39-121">Make sure that you have configured the firewall on the server instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to accept connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53f39-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="53f39-122">See Also</span></span>  
 <span data-ttu-id="53f39-123">[SQL Server 액세스를 허용 하도록 Windows 방화벽 구성](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md) </span><span class="sxs-lookup"><span data-stu-id="53f39-123">[Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md) </span></span>  
 <span data-ttu-id="53f39-124">[데이터베이스 엔진 액세스에 대 한 Windows 방화벽 구성](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) </span><span class="sxs-lookup"><span data-stu-id="53f39-124">[Configure a Windows Firewall for Database Engine Access](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) </span></span>  
 <span data-ttu-id="53f39-125">[클라이언트 프로토콜 구성](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="53f39-125">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 <span data-ttu-id="53f39-126">[네트워크 프로토콜 및 네트워크 라이브러리](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="53f39-126">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="53f39-127">[클라이언트 네트워크 구성](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="53f39-127">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="53f39-128">[클라이언트 프로토콜 구성](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="53f39-128">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="53f39-129">서버 네트워크 프로토콜 설정 또는 해제</span><span class="sxs-lookup"><span data-stu-id="53f39-129">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  

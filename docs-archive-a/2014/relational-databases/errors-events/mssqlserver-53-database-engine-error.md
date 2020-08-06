---
title: MSSQLSERVER_53 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "53"
helpviewer_keywords:
- 53 (Database Engine error)
ms.assetid: 1234f5a2-b3d1-425a-b29f-480fa792305f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 85fda292fb956047f51b9c7cd1d229ac0afce6b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651725"
---
# <a name="mssqlserver_53"></a><span data-ttu-id="b5ea5-102">MSSQLSERVER_53</span><span class="sxs-lookup"><span data-stu-id="b5ea5-102">MSSQLSERVER_53</span></span>
    
## <a name="details"></a><span data-ttu-id="b5ea5-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="b5ea5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b5ea5-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="b5ea5-104">Product Name</span></span>|<span data-ttu-id="b5ea5-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b5ea5-105">SQL Server</span></span>|  
|<span data-ttu-id="b5ea5-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="b5ea5-106">Event ID</span></span>|<span data-ttu-id="b5ea5-107">53</span><span class="sxs-lookup"><span data-stu-id="b5ea5-107">53</span></span>|  
|<span data-ttu-id="b5ea5-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="b5ea5-108">Event Source</span></span>|<span data-ttu-id="b5ea5-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b5ea5-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b5ea5-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="b5ea5-110">Component</span></span>|<span data-ttu-id="b5ea5-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b5ea5-111">SQLEngine</span></span>|  
|<span data-ttu-id="b5ea5-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="b5ea5-112">Symbolic Name</span></span>||  
|<span data-ttu-id="b5ea5-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="b5ea5-113">Message Text</span></span>|<span data-ttu-id="b5ea5-114">서버에 대한 연결을 구성하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ea5-114">An error has occurred while establishing a connection to the server.</span></span>  <span data-ttu-id="b5ea5-115">SQL Server에 연결할 때 기본 설정에서 SQL Server가 원격 연결을 허용하지 않기 때문에 이 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ea5-115">When connecting to SQL Server, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections.</span></span> <span data-ttu-id="b5ea5-116">(공급자: 명명된 파이프 공급자, 오류: 40 - SQL Server에 대한 연결을 열 수 없습니다.)(.Net SqlClient 데이터 공급자)</span><span class="sxs-lookup"><span data-stu-id="b5ea5-116">(provider: Named Pipes Provider, error: 40 - Could not open a connection to SQL Server) (.Net SqlClient Data Provider)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b5ea5-117">설명</span><span class="sxs-lookup"><span data-stu-id="b5ea5-117">Explanation</span></span>  
 <span data-ttu-id="b5ea5-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 클라이언트가 서버에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ea5-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client cannot connect to the server.</span></span> <span data-ttu-id="b5ea5-119">이 오류는 클라이언트가 서버 이름을 확인할 수 없거나 서버 이름이 잘못되어 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ea5-119">This error could occur because either the client cannot resolve the name of the server or the name of the server is incorrect.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b5ea5-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="b5ea5-120">User Action</span></span>  
 <span data-ttu-id="b5ea5-121">클라이언트에 올바른 서버 이름을 입력했는지 그리고 클라이언트에서 서버 이름을 확인할 수 있는지 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ea5-121">Make sure that you have entered the correct server name on the client, and that you can resolve the name of the server from the client.</span></span> <span data-ttu-id="b5ea5-122">TCP/IP 이름 확인을 검사하기 위해 Windows 운영 체제에서 **ping** 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ea5-122">To check TCP/IP name resolution, you can use the **ping** command in the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5ea5-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b5ea5-123">See Also</span></span>  
 <span data-ttu-id="b5ea5-124">[네트워크 프로토콜 및 네트워크 라이브러리](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="b5ea5-124">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="b5ea5-125">[클라이언트 네트워크 구성](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="b5ea5-125">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="b5ea5-126">[클라이언트 프로토콜 구성](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="b5ea5-126">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="b5ea5-127">서버 네트워크 프로토콜 설정 또는 해제</span><span class="sxs-lookup"><span data-stu-id="b5ea5-127">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  

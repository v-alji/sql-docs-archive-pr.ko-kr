---
title: MSSQLSERVER_2 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "2"
helpviewer_keywords:
- 2 (Database Engine error)
ms.assetid: 567fb571-7cda-4ce8-a702-cdff2df5d419
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 87d19a24219fda79de2cad4c06af4f1936b37b24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653923"
---
# <a name="mssqlserver_2"></a><span data-ttu-id="0e86f-102">MSSQLSERVER_2</span><span class="sxs-lookup"><span data-stu-id="0e86f-102">MSSQLSERVER_2</span></span>
    
## <a name="details"></a><span data-ttu-id="0e86f-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="0e86f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0e86f-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="0e86f-104">Product Name</span></span>|<span data-ttu-id="0e86f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="0e86f-105">SQL Server</span></span>|  
|<span data-ttu-id="0e86f-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="0e86f-106">Event ID</span></span>|<span data-ttu-id="0e86f-107">2</span><span class="sxs-lookup"><span data-stu-id="0e86f-107">2</span></span>|  
|<span data-ttu-id="0e86f-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="0e86f-108">Event Source</span></span>|<span data-ttu-id="0e86f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="0e86f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="0e86f-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="0e86f-110">Component</span></span>|<span data-ttu-id="0e86f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="0e86f-111">SQLEngine</span></span>|  
|<span data-ttu-id="0e86f-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="0e86f-112">Symbolic Name</span></span>||  
|<span data-ttu-id="0e86f-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="0e86f-113">Message Text</span></span>|<span data-ttu-id="0e86f-114">서버에 대한 연결을 구성하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="0e86f-114">An error has occurred while establishing a connection to the server.</span></span>  <span data-ttu-id="0e86f-115">SQL Server에 연결할 때 기본 설정에서 SQL Server가 원격 연결을 허용하지 않기 때문에 이 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e86f-115">When connecting to SQL Server, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections.</span></span> <span data-ttu-id="0e86f-116">(공급자: 명명된 파이프 공급자, 오류: 40 - SQL Server에 대한 연결을 열 수 없습니다.)(.Net SqlClient 데이터 공급자)</span><span class="sxs-lookup"><span data-stu-id="0e86f-116">(provider: Named Pipes Provider, error: 40 - Could not open a connection to SQL Server) (.Net SqlClient Data Provider)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0e86f-117">설명</span><span class="sxs-lookup"><span data-stu-id="0e86f-117">Explanation</span></span>  
 <span data-ttu-id="0e86f-118">아마도 서버가 시작되지 않았기 때문에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 클라이언트 요청에 응답하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="0e86f-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] did not respond to the client request because the server is probably not started.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0e86f-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="0e86f-119">User Action</span></span>  
 <span data-ttu-id="0e86f-120">서버가 시작되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0e86f-120">Make sure that the server is started.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e86f-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0e86f-121">See Also</span></span>  
 <span data-ttu-id="0e86f-122">[데이터베이스 엔진 서비스 관리](../../database-engine/configure-windows/manage-the-database-engine-services.md) </span><span class="sxs-lookup"><span data-stu-id="0e86f-122">[Manage the Database Engine Services](../../database-engine/configure-windows/manage-the-database-engine-services.md) </span></span>  
 <span data-ttu-id="0e86f-123">[클라이언트 프로토콜 구성](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="0e86f-123">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 <span data-ttu-id="0e86f-124">[네트워크 프로토콜 및 네트워크 라이브러리](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="0e86f-124">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="0e86f-125">[클라이언트 네트워크 구성](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="0e86f-125">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="0e86f-126">[클라이언트 프로토콜 구성](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="0e86f-126">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="0e86f-127">서버 네트워크 프로토콜 설정 또는 해제</span><span class="sxs-lookup"><span data-stu-id="0e86f-127">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  

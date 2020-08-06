---
title: MSSQLSERVER_17194 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "17194"
helpviewer_keywords:
- 17194 (Database Engine error)
ms.assetid: 0d03eb20-28a7-4ceb-8903-7f9420a620f7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d3f56a104841c4825bba1f60b3588fadd63555c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650078"
---
# <a name="mssqlserver_17194"></a><span data-ttu-id="278f7-102">MSSQLSERVER_17194</span><span class="sxs-lookup"><span data-stu-id="278f7-102">MSSQLSERVER_17194</span></span>
    
## <a name="details"></a><span data-ttu-id="278f7-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="278f7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="278f7-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="278f7-104">Product Name</span></span>|<span data-ttu-id="278f7-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="278f7-105">SQL Server</span></span>|  
|<span data-ttu-id="278f7-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="278f7-106">Event ID</span></span>|<span data-ttu-id="278f7-107">17194</span><span class="sxs-lookup"><span data-stu-id="278f7-107">17194</span></span>|  
|<span data-ttu-id="278f7-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="278f7-108">Event Source</span></span>|<span data-ttu-id="278f7-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="278f7-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="278f7-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="278f7-110">Component</span></span>|<span data-ttu-id="278f7-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="278f7-111">SQLEngine</span></span>|  
|<span data-ttu-id="278f7-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="278f7-112">Symbolic Name</span></span>||  
|<span data-ttu-id="278f7-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="278f7-113">Message Text</span></span>|<span data-ttu-id="278f7-114">서버에서 로그인에 필요한 SSL 공급자 라이브러리를 로드할 수 없습니다. 연결이 닫혔습니다.</span><span class="sxs-lookup"><span data-stu-id="278f7-114">The server was unable to load the SSL provider library needed to log in; the connection has been closed.</span></span> <span data-ttu-id="278f7-115">SSL은 관리자가 서버를 구성한 방식에 따라 로그인 시퀀스 또는 모든 통신을 암호화하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="278f7-115">SSL is used to encrypt either the login sequence or all communications, depending on how the administrator has configured the server.</span></span> <span data-ttu-id="278f7-116">온라인 설명서에서 다음 오류 메시지에 대한 정보를 확인하세요.  0xXXXX.</span><span class="sxs-lookup"><span data-stu-id="278f7-116">See Books Online for information on this error message:  0xXXXX.</span></span> <span data-ttu-id="278f7-117">[CLIENT: 11.11.11.11]</span><span class="sxs-lookup"><span data-stu-id="278f7-117">[CLIENT: 11.11.11.11]</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="278f7-118">설명</span><span class="sxs-lookup"><span data-stu-id="278f7-118">Explanation</span></span>  
 <span data-ttu-id="278f7-119">이 오류는 클라이언트가 연결을 닫았음을 나타내며</span><span class="sxs-lookup"><span data-stu-id="278f7-119">This error indicates that the client has closed the connection.</span></span> <span data-ttu-id="278f7-120">연결 제한 시간이 초과되어 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="278f7-120">This error could occur because the connection time-out has expired.</span></span> <span data-ttu-id="278f7-121">이 오류 메시지에는 근본 문제를 설명하는 운영 체제의 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="278f7-121">The error message displays a value from the operating system that describes the underlying problem.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="278f7-122">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="278f7-122">User Action</span></span>  
 <span data-ttu-id="278f7-123">메시지의 오류 코드가 0x2746(10진수 값 10054)이면 일반적으로 시간이 초과되어 클라이언트가 연결을 다시 설정했음을 의미합니다. 이 오류를 해결하려면 클라이언트나 호출 프로그램에서 연결 제한 시간을 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="278f7-123">If the error code in the message is 0x2746 (decimal value 10054), this means that the connection was reset by the client, typically because of a time-out. To resolve the error, increase the connection time-out on the client or calling program.</span></span>  
  
 <span data-ttu-id="278f7-124">다른 오류 메시지 값에 대해 사용 가능한 해결 방법을 확인하려면 운영 체제 명령 **net helpmsg**를 사용하고 오류 코드의 10진수 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="278f7-124">To determine a possible solution for other error message values, use the operating system command **net helpmsg** and specify the decimal value of the error code.</span></span>  
  
 <span data-ttu-id="278f7-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결하는 방법에 대한 자세한 내용은 [서버 네트워크 구성](../../database-engine/configure-windows/server-network-configuration.md) 및 [클라이언트 네트워크 구성](../../database-engine/configure-windows/client-network-configuration.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="278f7-125">For more information about how to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Server Network Configuration](../../database-engine/configure-windows/server-network-configuration.md) and [Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md).</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="278f7-126">내부 전용</span><span class="sxs-lookup"><span data-stu-id="278f7-126">Internal-Only</span></span>  
  

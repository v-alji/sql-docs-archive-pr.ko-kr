---
title: remote admin connections 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- administrator connections [SQL Server]
- DAC
- connections [SQL Server], dedicated administrator
- remote admin connections option
- dedicated administrator connections [SQL Server]
ms.assetid: bf32b60a-7a48-401f-b6be-b5e2e46c413f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c17cf278d18444c5b93d4f4b7e0a3da8dbfb671e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659641"
---
# <a name="remote-admin-connections-server-configuration-option"></a><span data-ttu-id="0586c-102">remote admin connections 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="0586c-102">remote admin connections Server Configuration Option</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0586c-103">는 DAC(관리자 전용 연결)를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0586c-103">provides a dedicated administrator connection (DAC).</span></span> <span data-ttu-id="0586c-104">DAC를 사용하면 서버가 잠겨 있거나 비정상적인 상태로 작동 중이어서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 연결에 응답하지 않는 경우에도 관리자가 실행 중인 서버에 액세스하여 진단 기능 또는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 문을 실행하거나 서버의 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0586c-104">The DAC lets an administrator access a running server to execute diagnostic functions or [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, or to troubleshoot problems on the server, even when the server is locked or running in an abnormal state and not responding to a [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] connection.</span></span> <span data-ttu-id="0586c-105">기본적으로 DAC는 서버의 클라이언트에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0586c-105">By default, the DAC is only available from a client on the server.</span></span> <span data-ttu-id="0586c-106">원격 컴퓨터의 클라이언트 애플리케이션에서 DAC를 사용할 수 있도록 하려면 sp_configure의 remote admin connections 옵션을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="0586c-106">To enable client applications on remote computers to use the DAC, use the remote admin connections option of sp_configure.</span></span>  
  
 <span data-ttu-id="0586c-107">기본적으로 DAC는 루프백 IP 주소(127.0.0.1), 포트 1434에서만 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="0586c-107">By default, the DAC only listens on the loop-back IP address (127.0.0.1), port 1434.</span></span> <span data-ttu-id="0586c-108">TCP 포트 1434를 사용할 수 없는 경우 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 이 시작되면 TCP 포트가 동적으로 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="0586c-108">If TCP port 1434 is not available, a TCP port is dynamically assigned when the [!INCLUDE[ssDE](../../includes/ssde-md.md)] starts up.</span></span> <span data-ttu-id="0586c-109">컴퓨터에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 둘 이상 설치되어 있으면 오류 로그에서 TCP 포트 번호를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="0586c-109">When more than one instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed on a computer, check the error log for the TCP port number.</span></span>  
  
 <span data-ttu-id="0586c-110">다음 표에서는 remote admin connections 옵션에 사용할 수 있는 값을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="0586c-110">The following table lists the possible values for the remote admin connections option.</span></span>  
  
|<span data-ttu-id="0586c-111">값</span><span class="sxs-lookup"><span data-stu-id="0586c-111">Value</span></span>|<span data-ttu-id="0586c-112">Description</span><span class="sxs-lookup"><span data-stu-id="0586c-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0586c-113">0</span><span class="sxs-lookup"><span data-stu-id="0586c-113">0</span></span>|<span data-ttu-id="0586c-114">DAC를 사용하여 로컬 연결만 허용됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0586c-114">Indicates only local connections are allowed by using the DAC.</span></span>|  
|<span data-ttu-id="0586c-115">1</span><span class="sxs-lookup"><span data-stu-id="0586c-115">1</span></span>|<span data-ttu-id="0586c-116">DAC를 사용하여 원격 연결이 허용됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0586c-116">Indicates remote connections are allowed by using the DAC.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0586c-117">예제</span><span class="sxs-lookup"><span data-stu-id="0586c-117">Example</span></span>  
 <span data-ttu-id="0586c-118">다음 예에서는 원격 컴퓨터에서 DAC를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0586c-118">The following example enables the DAC from a remote computer.</span></span>  
  
```  
sp_configure 'remote admin connections', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="0586c-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0586c-119">See Also</span></span>  
 [<span data-ttu-id="0586c-120">데이터베이스 관리자를 위한 진단 연결</span><span class="sxs-lookup"><span data-stu-id="0586c-120">Diagnostic Connection for Database Administrators</span></span>](diagnostic-connection-for-database-administrators.md)  
  
  

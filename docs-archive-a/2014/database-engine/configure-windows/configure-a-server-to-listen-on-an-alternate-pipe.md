---
title: 대체 파이프 (SQL Server 구성 관리자)에서 수신 하도록 서버 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Named Pipes [SQL Server], configuring
- listening [SQL Server], pipes
- pipes [SQL Server], alternate
- alternate pipes [SQL Server]
ms.assetid: 914f7491-e2be-4b0d-b3aa-fe5409cdbafa
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 57d70cf4cd1d7474b895aeb8cb144c885e8a0f99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646643"
---
# <a name="configure-a-server-to-listen-on-an-alternate-pipe-sql-server-configuration-manager"></a><span data-ttu-id="e922c-102">대체 파이프에서 수신하도록 서버 구성(SQL Server 구성 관리자)</span><span class="sxs-lookup"><span data-stu-id="e922c-102">Configure a Server to Listen on an Alternate Pipe (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="e922c-103">이 항목에서는 SQL Server 구성 관리자를 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 대체 파이프로 수신하도록 서버를 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e922c-103">This topic describes how to configure a server to listen on an alternate pipe in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="e922c-104">기본적으로 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 의 기본 인스턴스는 명명된 파이프 \\\\.\pipe\sql\query에서 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="e922c-104">By default, the default instance of [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] listens on named pipe \\\\.\pipe\sql\query.</span></span> <span data-ttu-id="e922c-105">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 및 [!INCLUDE[ssEW](../../includes/ssew-md.md)] 의 명명된 인스턴스는 다른 파이프에서 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="e922c-105">Named instances of [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and [!INCLUDE[ssEW](../../includes/ssew-md.md)] listen on other pipes.</span></span>  
  
 <span data-ttu-id="e922c-106">클라이언트 애플리케이션을 사용하여 특정한 명명된 파이프에 연결하는 방법에는 다음 3가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e922c-106">There are three ways to connect to a specific named pipe with a client application:</span></span>  
  
-   <span data-ttu-id="e922c-107">서버에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 서비스를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e922c-107">Run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service on the server.</span></span>  
  
-   <span data-ttu-id="e922c-108">클라이언트에서 별칭을 만들어 명명된 파이프를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e922c-108">Create an alias on the client, specifying the named pipe.</span></span>  
  
-   <span data-ttu-id="e922c-109">클라이언트가 사용자 지정 연결 문자열을 사용하여 연결하도록 프로그래밍합니다.</span><span class="sxs-lookup"><span data-stu-id="e922c-109">Program the client to connect using a custom connection string.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e922c-110">SQL Server 구성 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="e922c-110">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-configure-the-named-pipe-used-by-the-sql-server-database-engine"></a><span data-ttu-id="e922c-111">SQL Server 데이터베이스 엔진에서 사용하는 명명된 파이프를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="e922c-111">To configure the named pipe used by the SQL Server Database Engine</span></span>  
  
1.  <span data-ttu-id="e922c-112">SQL Server 구성 관리자의 콘솔 창에서 **SQL Server 네트워크 구성**을 확장한 다음 *\<instance name>* 에 대한 **프로토콜**을 클릭하여 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e922c-112">In SQL Server Configuration Manager, in the console pane, expand **SQL Server Network Configuration**, and then click expand **Protocols for** *\<instance name>*.</span></span>  
  
2.  <span data-ttu-id="e922c-113">세부 정보 창에서 **명명된 파이프**를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e922c-113">In the details pane, right-click **Named Pipes**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="e922c-114">**프로토콜** 탭의 **파이프 이름** 입력란에 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 이 수신하도록 할 파이프를 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e922c-114">On the **Protocol** tab, in the **Pipe Name** box, type the pipe you want the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to listen on, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="e922c-115">콘솔 창에서 **SQL Server 서비스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e922c-115">In the console pane, click **SQL Server Services**.</span></span>  
  
5.  <span data-ttu-id="e922c-116">세부 정보 창에서 **SQL Server(** \<instance name> **)** 를 마우스 오른쪽 단추로 클릭한 다음 **다시 시작**을 클릭하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 중지하고 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e922c-116">In the details pane, right-click **SQL Server (**\<instance name>**)** and then click **Restart**, to stop and restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="e922c-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 대체 파이프에서 수신하는 경우 클라이언트 애플리케이션을 사용하여 특정한 명명된 파이프에 연결하는 방법은 다음 세 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e922c-117">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is listening on an alternate pipe, there are three ways to connect to a specific named pipe with a client application:</span></span>  
  
-   <span data-ttu-id="e922c-118">서버에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 서비스를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e922c-118">Run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service on the server.</span></span>  
  
-   <span data-ttu-id="e922c-119">클라이언트에서 별칭을 만들어 명명된 파이프를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e922c-119">Create an alias on the client, specifying the named pipe.</span></span>  
  
-   <span data-ttu-id="e922c-120">클라이언트가 사용자 지정 연결 문자열을 사용하여 연결하도록 프로그래밍합니다.</span><span class="sxs-lookup"><span data-stu-id="e922c-120">Program the client to connect using a custom connection string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e922c-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e922c-121">See Also</span></span>  
 <span data-ttu-id="e922c-122">[클라이언트에서 사용할 서버 별칭 만들기 또는 삭제&#40;SQL Server 구성 관리자&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md) </span><span class="sxs-lookup"><span data-stu-id="e922c-122">[Create or Delete a Server Alias for Use by a Client &#40;SQL Server Configuration Manager&#41;](create-or-delete-a-server-alias-for-use-by-a-client.md) </span></span>  
 [<span data-ttu-id="e922c-123">서버 네트워크 구성</span><span class="sxs-lookup"><span data-stu-id="e922c-123">Server Network Configuration</span></span>](server-network-configuration.md)  
  
  

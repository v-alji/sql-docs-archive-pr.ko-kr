---
title: 연결된 서버 등록
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerserver.f1
helpviewer_keywords:
- Registered Servers [SQL Server], register connected servers
- connected server registrations [SQL Server]
ms.assetid: 77deb5f5-0f80-484f-8b8b-29afa67ec18f
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 1d337d2da7d305165307745fb02526e37b53bbd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649311"
---
# <a name="register-a-connected-server-sql-server-management-studio"></a><span data-ttu-id="09929-102">연결된 서버 등록(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="09929-102">Register a Connected Server (SQL Server Management Studio)</span></span>
  <span data-ttu-id="09929-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 서버를 등록하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="09929-103">This topic describes how to register servers in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="09929-104">서버를 등록하면 자주 액세스하는 서버에 대한 연결 정보를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09929-104">By registering the server, you can save the connection information for servers that you access frequently.</span></span> <span data-ttu-id="09929-105">개체 탐색기에서 연결하기 전이나 연결할 때 서버를 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09929-105">A server can be registered before connecting, or at the time of connection from Object Explorer.</span></span>  
  
 <span data-ttu-id="09929-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="09929-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="09929-107">**다음을 사용하여 서버를 등록합니다.**</span><span class="sxs-lookup"><span data-stu-id="09929-107">**To register a server, using:**</span></span>  
  
     [<span data-ttu-id="09929-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="09929-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="09929-109">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="09929-109">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-register-a-connected-server"></a><span data-ttu-id="09929-110">연결된 서버를 등록하려면</span><span class="sxs-lookup"><span data-stu-id="09929-110">To register a connected server</span></span>  
  
1.  <span data-ttu-id="09929-111">개체 탐색기에서 이미 연결된 서버를 마우스 오른쪽 단추로 클릭한 후에 **등록**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="09929-111">In Object Explorer, right-click a server to which you already are connected, and then click **Register**.</span></span>  
  
     <span data-ttu-id="09929-112">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="09929-112">**Server name**</span></span>  
     <span data-ttu-id="09929-113">등록된 서버에 사용할 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="09929-113">Enter the name you want to use for the registered server.</span></span> <span data-ttu-id="09929-114">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 로컬 서버 또는 원격 서버를 등록하면 다음에 연결할 때 사용하도록 서버 연결 정보를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09929-114">Registering a local or remote server using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] lets you store the server connection information for future connections.</span></span> <span data-ttu-id="09929-115">이 필드의 값은 서버에 연결할 때 사용자가 입력한 서버 이름으로 기본 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09929-115">This field defaults to the server name entered when you were connecting to the server.</span></span> <span data-ttu-id="09929-116">이 서버 이름을 그대로 사용하거나 사용하기 쉬운 다른 서버 이름을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09929-116">You can retain this server name or enter another easy-to-use name for the server.</span></span>  
  
     <span data-ttu-id="09929-117">**서버 설명**</span><span class="sxs-lookup"><span data-stu-id="09929-117">**Server description**</span></span>  
     <span data-ttu-id="09929-118">서버에 대한 선택적 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="09929-118">Enter an optional description of the server.</span></span> <span data-ttu-id="09929-119">250자까지 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09929-119">The maximum number of characters allowed is 250.</span></span>  
  
     <span data-ttu-id="09929-120">**서버 그룹을 선택하세요.**</span><span class="sxs-lookup"><span data-stu-id="09929-120">**Select a server group**</span></span>  
     <span data-ttu-id="09929-121">서버 등록을 저장할 서버 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="09929-121">Select the server group where you want to save the server registration.</span></span>  
  
     <span data-ttu-id="09929-122">**새 그룹**</span><span class="sxs-lookup"><span data-stu-id="09929-122">**New Group**</span></span>  
     <span data-ttu-id="09929-123">등록된 서버를 저장할 새 서버 그룹을 만드는 **새 그룹** 대화 상자를 시작하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="09929-123">Click to launch the **New Group** dialog box, where you can create a new server group for the registered server.</span></span>  
  
     <span data-ttu-id="09929-124">**저장**</span><span class="sxs-lookup"><span data-stu-id="09929-124">**Save**</span></span>  
     <span data-ttu-id="09929-125">입력한 정보를 저장하고 등록된 서버를 만들려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="09929-125">Click to save the information you have entered and create a registered server.</span></span>  
  
  

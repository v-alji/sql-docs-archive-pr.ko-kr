---
title: 클라이언트에서 사용할 서버 별칭 만들기 또는 삭제 (SQL Server 구성 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- server alias
helpviewer_keywords:
- aliases [SQL Server], deleting
- aliases [SQL Server], creating
ms.assetid: b687e376-ee33-470d-b65a-87246bfefe6f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: bead257b40c33e3640b18890a7d109d774131123
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651901"
---
# <a name="create-or-delete-a-server-alias-for-use-by-a-client-sql-server-configuration-manager"></a><span data-ttu-id="5ef82-102">클라이언트에서 사용할 서버 별칭 만들기 또는 삭제(SQL Server 구성 관리자)</span><span class="sxs-lookup"><span data-stu-id="5ef82-102">Create or Delete a Server Alias for Use by a Client (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="5ef82-103">이 항목에서는 SQL Server 구성 관리자를 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 서버 별칭을 만들거나 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef82-103">This topic describes how to create or delete a server alias in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="5ef82-104">별칭은 연결 설정에 사용할 수 있는 대체 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5ef82-104">An alias is an alternate name that can be used to make a connection.</span></span> <span data-ttu-id="5ef82-105">별칭은 연결 문자열의 필수 요소를 캡슐화하고 사용자가 선택한 이름으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="5ef82-105">The alias encapsulates the required elements of a connection string, and exposes them with a name chosen by the user.</span></span> <span data-ttu-id="5ef82-106">별칭은 모든 클라이언트 애플리케이션에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef82-106">Aliases can be used with any client application.</span></span> <span data-ttu-id="5ef82-107">서버 별칭을 만들면 서버별로 프로토콜과 연결 정보를 지정하지 않아도 클라이언트 컴퓨터가 각기 다른 네트워크 프로토콜을 사용하여 여러 대의 서버에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef82-107">By creating server aliases, your client computer can connect to multiple servers using different network protocols, without having to specify the protocol and connection details for each one.</span></span> <span data-ttu-id="5ef82-108">또한 여러 네트워크 프로토콜을 자주 사용하지 않더라도 이러한 프로토콜을 항상 사용 가능한 상태로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef82-108">In addition, you can also have different network protocols enabled all the time, even if you only need to use them occasionally.</span></span> <span data-ttu-id="5ef82-109">기본값이 아닌 포트 번호나 명명된 파이프에서 수신하도록 서버를 구성하고 SQL Server Browser 서비스를 사용하지 않도록 설정한 경우 새로운 포트 번호나 명명된 파이프를 지정하는 별칭을 만드십시오.</span><span class="sxs-lookup"><span data-stu-id="5ef82-109">If you have configured the server to listen on a non-default port number or named pipe, and you have disabled the SQL Server Browser service, create an alias that specifies the new port number or named pipe.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5ef82-110">SQL Server 구성 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="5ef82-110">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-create-an-alias"></a><span data-ttu-id="5ef82-111">별칭을 만들려면</span><span class="sxs-lookup"><span data-stu-id="5ef82-111">To create an alias</span></span>  
  
1.  <span data-ttu-id="5ef82-112">SQL Server 구성 관리자에서 **SQL Server Native Client 구성**을 확장하고 **별칭**을 마우스 오른쪽 단추로 클릭한 다음 **새 별칭**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef82-112">In SQL Server Configuration Manager, expand **SQL Server Native Client Configuration**, right-click **Aliases**, and then click **New Alias**.</span></span>  
  
2.  <span data-ttu-id="5ef82-113">**별칭** 상자에 별칭 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef82-113">In the **Alias Name** box, type the name of the alias.</span></span> <span data-ttu-id="5ef82-114">클라이언트 애플리케이션은 연결할 때 이 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef82-114">Client applications use this name when they connect.</span></span>  
  
3.  <span data-ttu-id="5ef82-115">**서버** 상자에 서버 이름이나 IP 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef82-115">In the **Server** box, type the name or IP address of a server.</span></span> <span data-ttu-id="5ef82-116">명명된 인스턴트에 인스턴트 이름을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef82-116">For a named instance append the instance name.</span></span>  
  
4.  <span data-ttu-id="5ef82-117">**프로토콜** 상자에서 이 별칭에 사용되는 프로토콜을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef82-117">In the **Protocol** box, select the protocol used for this alias.</span></span> <span data-ttu-id="5ef82-118">프로토콜을 선택하면 옵션 속성 상자 제목이 포트 번호, 파이프 이름 또는 연결 문자열로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="5ef82-118">Selecting a protocol, changes the title of the optional properties box to Port No, Pipe Name, or Connection String.</span></span>  
  
 <span data-ttu-id="5ef82-119">자신의 연결 문자열을 만들 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자 도움말에 설명되어 있는 연결 문자열을 참조하면 많은 도움이 될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5ef82-119">The connection strings described in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager Help can be useful for programmers who create their own connection strings.</span></span> <span data-ttu-id="5ef82-120">이 정보에 액세스하려면 **새 별칭** 대화 상자에서 F1을 누르거나 **도움말**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef82-120">To access this information, in the **New Alias** dialog box, press F1, or click **Help**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5ef82-121">구성된 별칭이 잘못된 서버나 인스턴스에 연결되어 있으면 관련 네트워크 프로토콜을 사용하지 못하게 한 다음 다시 사용 가능하게 하십시오.</span><span class="sxs-lookup"><span data-stu-id="5ef82-121">If a configured alias is connecting to the wrong server or instance, disable and then reenable the associated network protocol.</span></span> <span data-ttu-id="5ef82-122">그러면 캐시된 연결 정보가 지워지고 클라이언트에서 올바르게 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef82-122">Doing this clears any cached connection information and allows the client to connect correctly.</span></span>  
  
#### <a name="to-delete-an-alias"></a><span data-ttu-id="5ef82-123">별칭을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="5ef82-123">To delete an alias</span></span>  
  
1.  <span data-ttu-id="5ef82-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자에서 **SQL Server Native Client 구성**을 확장한 다음 **별칭**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef82-124">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, expand **SQL Server Native Client Configuration**, and then click **Aliases**.</span></span>  
  
2.  <span data-ttu-id="5ef82-125">세부 정보 창에서 삭제할 별칭을 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef82-125">In the details pane, right-click the alias that you want to delete, and then click **Delete**.</span></span>  
  
  

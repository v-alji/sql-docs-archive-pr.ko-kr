---
title: 명령 취소 (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- connections [XML for Analysis]
- associated connections [XML for Analysis]
- XML for Analysis, canceling
- associated sessions [XML for Analysis]
- canceling connections
- canceling commands
- canceling sessions
- SPID
- XMLA, canceling
- server process IDs [XML for Analysis]
- sessions [XML for Analysis]
ms.assetid: b59f8197-c33d-4e65-9022-848ccba540f5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 003c70362c38ae1838b4679abf6485fa031a9143
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728900"
---
# <a name="canceling-commands-xmla"></a><span data-ttu-id="7e73d-102">명령 취소(XMLA)</span><span class="sxs-lookup"><span data-stu-id="7e73d-102">Canceling Commands (XMLA)</span></span>
  <span data-ttu-id="7e73d-103">명령을 실행 하는 사용자의 관리 권한에 따라 XMLA (XML for Analysis)의 [Cancel](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla) 명령은 세션, 세션, 연결, 서버 프로세스 또는 연결 된 세션 또는 연결에서 명령을 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e73d-103">Depending on the administrative permissions of the user issuing the command, the [Cancel](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla) command in XML for Analysis (XMLA) can cancel a command on a session, a session, a connection, a server process, or an associated session or connection.</span></span>  
  
## <a name="canceling-commands"></a><span data-ttu-id="7e73d-104">명령 취소</span><span class="sxs-lookup"><span data-stu-id="7e73d-104">Canceling Commands</span></span>  
 <span data-ttu-id="7e73d-105">사용자는 속성을 지정하지 않고 `Cancel` 명령을 보내어 현재 명시적 세션의 컨텍스트 내에서 현재 실행 중인 명령을 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e73d-105">A user can cancel the currently executing command within the context of the current explicit session by sending a `Cancel` command with no specified properties.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7e73d-106">암시적 세션에서 실행 중인 명령은 사용자가 취소할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e73d-106">A command running in an implicit session cannot be canceled by a user.</span></span>  
  
### <a name="canceling-batch-commands"></a><span data-ttu-id="7e73d-107">Batch 명령 취소</span><span class="sxs-lookup"><span data-stu-id="7e73d-107">Canceling Batch Commands</span></span>  
 <span data-ttu-id="7e73d-108">사용자가 `Batch` 명령을 취소하면 `Batch` 명령 내에서 아직 실행되지 않고 남아 있는 모든 명령이 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e73d-108">If a user cancels a `Batch` command, then all remaining commands not yet executed within the `Batch` command are canceled.</span></span> <span data-ttu-id="7e73d-109">`Batch` 명령이 트랜잭션인 경우 `Cancel` 명령이 실행되기 전에 실행된 모든 명령은 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e73d-109">If the `Batch` command was transactional, any commands that were executed before the `Cancel` command runs are rolled back.</span></span>  
  
## <a name="canceling-sessions"></a><span data-ttu-id="7e73d-110">세션 취소</span><span class="sxs-lookup"><span data-stu-id="7e73d-110">Canceling Sessions</span></span>  
 <span data-ttu-id="7e73d-111">명령의 [SessionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) 속성에 명시적 세션에 대 한 세션 식별자를 지정 하 여 `Cancel` 데이터베이스 관리자나 서버 관리자는 현재 실행 중인 명령을 포함 하 여 세션을 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e73d-111">By specifying a session identifier for an explicit session in the [SessionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) property of the `Cancel` command, a database administrator or server administrator can cancel a session, including the currently executing command.</span></span> <span data-ttu-id="7e73d-112">데이터베이스 관리자는 자신이 관리 권한을 가지고 있는 데이터베이스에 대한 세션만을 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e73d-112">A database administrator can only cancel sessions for databases on which he or she has administrative permissions.</span></span>  
  
 <span data-ttu-id="7e73d-113">데이터베이스 관리자는 DISCOVER_SESSIONS 스키마 행 집합을 검색하여 지정된 데이터베이스의 활성 세션을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e73d-113">A database administrator can retrieve the active sessions for a specified database by retrieving the DISCOVER_SESSIONS schema rowset.</span></span> <span data-ttu-id="7e73d-114">DISCOVER_SESSIONS 스키마 행 집합을 검색 하기 위해 데이터베이스 관리자는 XMLA 메서드를 사용 하 `Discover` 고 메서드의 restriction 속성에 있는 SESSION_CURRENT_DATABASE restriction 열에 대해 [Restrictions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/restrictions-element-xmla) 적절 한 데이터베이스 식별자를 지정 합니다 `Discover` .</span><span class="sxs-lookup"><span data-stu-id="7e73d-114">To retrieve the DISCOVER_SESSIONS schema rowset, the database administrator uses the XMLA `Discover` method and specifies the appropriate database identifier for the SESSION_CURRENT_DATABASE restriction column in the [Restrictions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/restrictions-element-xmla) property of the `Discover` method.</span></span>  
  
## <a name="canceling-connections"></a><span data-ttu-id="7e73d-115">연결 취소</span><span class="sxs-lookup"><span data-stu-id="7e73d-115">Canceling Connections</span></span>  
 <span data-ttu-id="7e73d-116">서버 관리자는 명령의 [ConnectionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/connectionid-element-xmla) 속성에 연결 식별자를 지정 하 여 `Cancel` 실행 중인 모든 명령을 포함 하 여 지정 된 연결과 관련 된 모든 세션을 취소 하 고 연결을 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e73d-116">By specifying a connection identifier in the [ConnectionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/connectionid-element-xmla) property of the `Cancel` command, a server administrator can cancel all of the sessions associated with a given connection, including all running commands, and cancel the connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7e73d-117">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] HTTP 연결을 제공 하는 동안 데이터 펌프가 여러 세션을 여는 경우와 같이 인스턴스에서 연결에 연결 된 세션을 찾아 취소할 수 없는 경우 해당 인스턴스는 연결을 취소할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e73d-117">If the instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] cannot locate and cancel the sessions associated with a connection, such as when the data pump opens multiple sessions while providing HTTP connectivity, the instance cannot cancel the connection.</span></span> <span data-ttu-id="7e73d-118">`Cancel` 명령을 실행하는 동안 이런 경우가 발생하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="7e73d-118">If this case is encountered during the execution of a `Cancel` command, an error occurs.</span></span>  
  
 <span data-ttu-id="7e73d-119">서버 관리자는 XMLA `Discover` 메서드를 통해 DISCOVER_CONNECTIONS 스키마 행 집합을 검색하여 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스의 활성 세션을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e73d-119">A server administrator can retrieve the active connections for an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance by retrieving the DISCOVER_CONNECTIONS schema rowset using the XMLA `Discover` method.</span></span>  
  
## <a name="canceling-server-processes"></a><span data-ttu-id="7e73d-120">서버 프로세스 취소</span><span class="sxs-lookup"><span data-stu-id="7e73d-120">Canceling Server Processes</span></span>  
 <span data-ttu-id="7e73d-121">명령의 [spid](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) 속성에서 spid (서버 프로세스 식별자)를 지정 하면 `Cancel` 서버 관리자가 지정 된 SPID와 연결 된 명령을 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e73d-121">By specifying a server process identifier (SPID) in the [SPID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) property of the `Cancel` command, a server administrator can cancel the commands associated with a given SPID.</span></span>  
  
## <a name="canceling-associated-sessions-and-connections"></a><span data-ttu-id="7e73d-122">연관된 세션 및 연결 취소</span><span class="sxs-lookup"><span data-stu-id="7e73d-122">Canceling Associated Sessions and Connections</span></span>  
 <span data-ttu-id="7e73d-123">[Cancelassociated](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cancelassociated-element-xmla) 속성을 true로 설정 하 여 명령에 지정 된 연결, 세션 또는 SPID와 연결 된 연결, 세션 및 명령을 취소할 수 있습니다 `Cancel` .</span><span class="sxs-lookup"><span data-stu-id="7e73d-123">You can set the [CancelAssociated](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cancelassociated-element-xmla) property to true to cancel the connections, sessions, and commands associated with the connection, session, or SPID specified in the `Cancel` command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e73d-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7e73d-124">See Also</span></span>  
 <span data-ttu-id="7e73d-125">[XMLA&#41;&#40;메서드를 검색 합니다.](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) </span><span class="sxs-lookup"><span data-stu-id="7e73d-125">[Discover Method &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) </span></span>  
 [<span data-ttu-id="7e73d-126">Analysis Services에서 XMLA를 사용하여 개발</span><span class="sxs-lookup"><span data-stu-id="7e73d-126">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  

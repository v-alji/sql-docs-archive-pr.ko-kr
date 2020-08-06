---
title: 일반 연결 및 컨텍스트 연결 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: a1dead02-be88-4b16-8cb2-db1284856764
author: rothja
ms.author: jroth
ms.openlocfilehash: ce531129099a8f4908bdc4b29920696d4ba3c505
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661170"
---
# <a name="regular-vs-context-connections"></a><span data-ttu-id="0d482-102">일반 연결 및 컨텍스트 연결</span><span class="sxs-lookup"><span data-stu-id="0d482-102">Regular vs. Context Connections</span></span>
  <span data-ttu-id="0d482-103">원격 서버에 연결할 때는 컨텍스트 연결 대신 항상 일반 연결을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="0d482-103">If you are connecting to a remote server, always use regular connections rather than context connections.</span></span> <span data-ttu-id="0d482-104">컨텍스트 연결은 대개 저장 프로시저나 함수가 실행 중인 동일한 서버에 연결해야 하는 경우 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0d482-104">If you need to connect to the same server on which the stored procedure or function is running, use the context connection in most cases.</span></span> <span data-ttu-id="0d482-105">컨텍스트 연결을 사용하면 동일한 트랜잭션 공간에서 실행되므로 다시 인증할 필요가 없다는 장점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d482-105">This has benefits such as running in the same transaction space and not having to reauthenticate.</span></span>  
  
 <span data-ttu-id="0d482-106">또한 성능이 향상되고 리소스 사용량이 줄어드는 이점도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d482-106">Additionally, using the context connection typically results in better performance and less resource usage.</span></span> <span data-ttu-id="0d482-107">컨텍스트 연결은 in-process 전용 연결 이므로 네트워크 프로토콜 및 전송 계층을 무시 하 여 서버에 "직접 연결" 하 여 Transact-sql 문을 보내고 결과를 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d482-107">The context connection is an in-process-only connection, so it can contact the server "directly" by bypassing the network protocol and transport layers to send Transact-SQL statements and receive results.</span></span> <span data-ttu-id="0d482-108">인증 프로세스도 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d482-108">The authentication process is bypassed, as well.</span></span> <span data-ttu-id="0d482-109">다음 그림에서는 `SqlClient` 관리 공급자의 주요 구성 요소와 함께 일반 연결을 사용할 때와 컨텍스트 연결을 사용할 때 다양한 구성 요소가 서로 어떻게 상호 작용하는지 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0d482-109">The following figure shows the primary components of the `SqlClient` managed provider, as well as how the different components interact with each other when using a regular connection, and when using the context connection.</span></span>  
  
 <span data-ttu-id="0d482-110">![컨텍스트 및 일반 연결의 코드 경로](../../../database-engine/dev-guide/media/clrintdataaccess.gif "컨텍스트 및 일반 연결의 코드 경로")</span><span class="sxs-lookup"><span data-stu-id="0d482-110">![Code paths of a context and a regular connnection.](../../../database-engine/dev-guide/media/clrintdataaccess.gif "Code paths of a context and a regular connnection.")</span></span>  
  
 <span data-ttu-id="0d482-111">컨텍스트 연결은 보다 짧은 코드 경로를 따르고 관련되는 구성 요소가 적으므로 일반 연결보다 빠르게 서버로 요청을 보내고 결과를 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d482-111">The context connection follows a shorter code path and involves fewer components, so you can expect requests and results to get to and from the server faster than in a regular connection.</span></span> <span data-ttu-id="0d482-112">서버의 쿼리 실행 시간은 컨텍스트 연결을 사용할 때와 일반 연결을 사용할 때 모두 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0d482-112">Query execution time on the server is the same for context and regular connections.</span></span>  
  
 <span data-ttu-id="0d482-113">동일한 서버에 대해 별도의 일반 연결을 열어야 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d482-113">There are some cases in which you may need to open a separate regular connection to the same server.</span></span> <span data-ttu-id="0d482-114">예를 들어 [일반 및 컨텍스트 연결에 대 한 제한 사항](context-connections-and-regular-connections-restrictions.md)에 설명 된 대로 컨텍스트 연결 사용에 대 한 특정 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d482-114">For example, there are certain restrictions on using the context connection, described in [Restrictions on Regular and Context Connections](context-connections-and-regular-connections-restrictions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d482-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0d482-115">See Also</span></span>  
 [<span data-ttu-id="0d482-116">컨텍스트 연결</span><span class="sxs-lookup"><span data-stu-id="0d482-116">Context Connection</span></span>](context-connection.md)  
  
  

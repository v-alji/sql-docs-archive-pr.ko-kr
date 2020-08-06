---
title: 일반 및 컨텍스트 연결에 대 한 제한 사항 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: 0c6fe4cb-d846-40b5-8884-35a9c770f5e8
author: rothja
ms.author: jroth
ms.openlocfilehash: 52f50347a27cdaffe83b252d86c56382b5ef4f31
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652163"
---
# <a name="restrictions-on-regular-and-context-connections"></a><span data-ttu-id="0434c-102">일반 연결 및 컨텍스트 연결에 대한 제한 사항</span><span class="sxs-lookup"><span data-stu-id="0434c-102">Restrictions on Regular and Context Connections</span></span>
  <span data-ttu-id="0434c-103">이 항목에서는 [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] 프로세스에서 컨텍스트 및 일반 연결을 통한 코드 실행과 관련된 제한 사항을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0434c-103">This topic discusses the restrictions associated with code executing in the [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] process through context and regular connections.</span></span>  
  
## <a name="restrictions-on-context-connections"></a><span data-ttu-id="0434c-104">컨텍스트 연결에 대한 제한 사항</span><span class="sxs-lookup"><span data-stu-id="0434c-104">Restrictions on Context Connections</span></span>  
 <span data-ttu-id="0434c-105">애플리케이션을 개발할 때는 컨텍스트 연결에 적용되는 다음과 같은 제한 사항을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0434c-105">When developing your application, take into account the following restrictions that apply to context connections:</span></span>  
  
-   <span data-ttu-id="0434c-106">지정된 시간에 지정된 연결에 대해 하나의 컨텍스트 연결만 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0434c-106">You can have only one context connection open at a given time for a given connection.</span></span> <span data-ttu-id="0434c-107">별도의 연결에서 여러 문을 동시에 실행하는 경우 각 문에 대해 자체의 컨텍스트 연결이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="0434c-107">If you have multiple statements running concurrently in separate connections, each one of them can get their own context connection.</span></span> <span data-ttu-id="0434c-108">이 제한 사항은 다른 연결의 동시 요청에는 적용되지 않으며 지정된 연결의 지정된 요청에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0434c-108">The restriction does not affect concurrent requests from different connections; it only affects a given request on a given connection.</span></span>  
  
-   <span data-ttu-id="0434c-109">컨텍스트 연결에서는 MARS(Multiple Active Result Sets)가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0434c-109">Multiple Active Result Sets (MARS) is not supported in a context connection.</span></span>  
  
-   <span data-ttu-id="0434c-110">`SqlBulkCopy` 클래스는 컨텍스트 연결에서 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0434c-110">The `SqlBulkCopy` class does not operate in a context connection.</span></span>  
  
-   <span data-ttu-id="0434c-111">컨텍스트 연결에서는 업데이트 일괄 처리가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0434c-111">Update batching in a context connection is not supported</span></span>  
  
-   <span data-ttu-id="0434c-112">`SqlNotificationRequest`는 컨텍스트 연결에 대해 실행되는 명령과 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0434c-112">`SqlNotificationRequest` cannot be used with commands that execute against a context connection.</span></span>  
  
-   <span data-ttu-id="0434c-113">컨텍스트 연결에 대해 실행되고 있는 명령은 취소할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0434c-113">Canceling commands that are running against the context connection is not supported.</span></span> <span data-ttu-id="0434c-114">`SqlCommand.Cancel` 메서드는 요청을 자동으로 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="0434c-114">The `SqlCommand.Cancel` method silently ignores the request.</span></span>  
  
-   <span data-ttu-id="0434c-115">"context connection=true"를 사용하는 경우 다른 연결 문자열 키워드를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0434c-115">No other connection string keywords can be used when you use "context connection=true".</span></span>  
  
-   <span data-ttu-id="0434c-116">`SqlConnection.DataSource` 속성은 `SqlConnection`의 연결 문자열이 "context connection=true"인 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 이름 대신 Null을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0434c-116">The `SqlConnection.DataSource` property returns null if the connection string for the `SqlConnection` is "context connection=true", instead of the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="0434c-117">명령이 컨텍스트 연결에 대해 실행되는 경우에는 `SqlCommand.CommandTimeout` 속성을 설정해도 아무 영향이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0434c-117">Setting the `SqlCommand.CommandTimeout` property has no effect when the command is executed against a context connection.</span></span>  
  
## <a name="restrictions-on-regular-connections"></a><span data-ttu-id="0434c-118">일반 연결에 대한 제한 사항</span><span class="sxs-lookup"><span data-stu-id="0434c-118">Restrictions on Regular Connections</span></span>  
 <span data-ttu-id="0434c-119">애플리케이션을 개발할 때는 일반 연결에 적용되는 다음과 같은 제한 사항을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0434c-119">When developing your application, take into account the following restrictions that apply to regular connections:</span></span>  
  
-   <span data-ttu-id="0434c-120">내부 서버에 대한 비동기 명령 실행이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0434c-120">Asynchronous command execution against internal servers is not supported.</span></span> <span data-ttu-id="0434c-121">명령의 연결 문자열에 "async=true"를 포함한 다음, 명령을 실행하면 `System.NotSupportedException`이 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="0434c-121">Including "async=true" in the connection string of a command, and then executing the command, results in `System.NotSupportedException` being thrown.</span></span> <span data-ttu-id="0434c-122">그리고 " [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 프로세스 내에서 실행할 경우 비동기 처리가 지원되지 않습니다"라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0434c-122">This message appears: "Asynchronous processing is not supported when running inside the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] process."</span></span>  
  
-   <span data-ttu-id="0434c-123">`SqlDependency` 개체가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0434c-123">`SqlDependency` object is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0434c-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0434c-124">See Also</span></span>  
 [<span data-ttu-id="0434c-125">컨텍스트 연결</span><span class="sxs-lookup"><span data-stu-id="0434c-125">Context Connection</span></span>](context-connection.md)  
  
  

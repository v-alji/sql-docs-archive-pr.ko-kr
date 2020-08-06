---
title: 데이터 원본에서 연결을 끊는 중 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC data sources, connections
- data sources [SQL Server Native Client]
- disconnecting [ODBC]
- ODBC applications, disconnecting
- SQLDisconnect function
- ODBC applications, data sources
- connections [SQL Server Native Client]
- SQLFreeHandle function
- ODBC data sources, disconnecting
- SQL Server Native Client ODBC driver, data sources
- ODBC functions
- SQL Server Native Client ODBC driver, connections
ms.assetid: 65b0267d-b2ab-4a59-83f2-436d90cfbf79
author: rothja
ms.author: jroth
ms.openlocfilehash: 5db3b83ab65d854f3a4d2182d9a4a1314e097681
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650942"
---
# <a name="disconnecting-from-a-data-source"></a><span data-ttu-id="10b50-102">데이터 원본에서 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="10b50-102">Disconnecting from a Data Source</span></span>
  <span data-ttu-id="10b50-103">응용 프로그램이 데이터 원본 사용을 마치면 **Sqldisconnect**를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="10b50-103">When an application has finished using a data source, it calls **SQLDisconnect**.</span></span> <span data-ttu-id="10b50-104">**Sqldisconnect** 는 연결에 할당 된 모든 문을 해제 하 고 데이터 원본에서 드라이버의 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="10b50-104">**SQLDisconnect** frees any statements that are allocated on the connection and disconnects the driver from the data source.</span></span> <span data-ttu-id="10b50-105">연결을 끊은 후 응용 프로그램은 [Sqlfreehandle](../native-client-odbc-api/sqlfreehandle.md) 을 호출 하 여 연결 핸들을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10b50-105">After disconnecting, the application can call [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) to free the connection handle.</span></span> <span data-ttu-id="10b50-106">종료 하기 전에 응용 프로그램은 **Sqlfreehandle** 을 호출 하 여 환경 핸들을 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="10b50-106">Before exiting, an application also calls **SQLFreeHandle** to free the environment handle.</span></span>  
  
 <span data-ttu-id="10b50-107">연결을 끊은 후 애플리케이션에서 할당된 연결 핸들을 다시 사용하여 다른 데이터 원본에 연결하거나 동일한 데이터 원본에 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10b50-107">After disconnecting, an application can reuse the allocated connection handle, either to connect to a different data source or reconnect to the same data source.</span></span> <span data-ttu-id="10b50-108">연결을 끊은 후 나중에 다시 연결하는 대신 연결된 상태로 유지할지 여부를 결정하는 경우 애플리케이션 작성기에서 각 옵션의 상대 비용을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10b50-108">The decision to remain connected instead of disconnecting and reconnecting later requires that the application writer consider the relative costs of each option.</span></span> <span data-ttu-id="10b50-109">데이터 원본에 연결하여 연결된 상태로 유지하는 것은 연결 매체에 따라 비교적 비용이 높을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10b50-109">Connecting to a data source and remaining connected can be relatively costly, depending on the connection medium.</span></span> <span data-ttu-id="10b50-110">장단점을 고려할 때 애플리케이션은 동일한 데이터 원본에서 추가 작업이 수행될 확률과 타이밍에 대해서도 가정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10b50-110">In making a trade-off, the application must also make assumptions about the probability and timing of additional operations on the same data source.</span></span> <span data-ttu-id="10b50-111">한 애플리케이션에서 둘 이상의 연결을 사용해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10b50-111">An application may also have to use more than one connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10b50-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="10b50-112">See Also</span></span>  
 [<span data-ttu-id="10b50-113">SQL Server &#40;ODBC&#41;와 통신</span><span class="sxs-lookup"><span data-stu-id="10b50-113">Communicating with SQL Server &#40;ODBC&#41;</span></span>](communicating-with-sql-server-odbc.md)  
  
  

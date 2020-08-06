---
title: SQL Server와 통신 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, communicating with SQL Server
- ODBC applications, communicating with SQL Server
- ODBC, communicating with SQL Server
ms.assetid: cca3dcf0-2a7e-465a-84de-7ce055360eb6
author: rothja
ms.author: jroth
ms.openlocfilehash: c41ac2dcce9c5bdbdd351148d16bcaa8f067d22f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738368"
---
# <a name="communicating-with-sql-server-odbc"></a><span data-ttu-id="2d667-102">SQL Server와 통신(ODBC)</span><span class="sxs-lookup"><span data-stu-id="2d667-102">Communicating with SQL Server (ODBC)</span></span>
  <span data-ttu-id="2d667-103">ODBC 응용 프로그램에서 인스턴스와 통신 하려면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 환경 및 연결 핸들을 할당 하 고 데이터 원본에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d667-103">For an ODBC application to communicate with an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], it must allocate environment and connection handles and connect to the data source.</span></span> <span data-ttu-id="2d667-104">연결이 설정되면 애플리케이션에서는 서버에 쿼리를 보내고 모든 결과 집합을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d667-104">After a connection is established, the application can send queries to the server and process any result sets.</span></span> <span data-ttu-id="2d667-105">데이터 원본 사용을 마치면 애플리케이션은 데이터 원본에 대한 연결을 끊고 연결 핸들을 해제한 후</span><span class="sxs-lookup"><span data-stu-id="2d667-105">When the application has finished using the data source, it disconnects from the data source and frees the connection handle.</span></span> <span data-ttu-id="2d667-106">연결 핸들이 모두 해제되면 환경 핸들을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="2d667-106">When the application has freed all its connection handles, it frees the environment handle.</span></span>  
  
 <span data-ttu-id="2d667-107">애플리케이션에서는 개수에 제한 없이 여러 데이터 원본에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d667-107">An application can connect to any number of data sources.</span></span> <span data-ttu-id="2d667-108">애플리케이션은 여러 드라이버와 여러 데이터 원본의 조합, 단일 드라이버와 여러 데이터 원본 조합 또는 단일 드라이버와 단일 데이터 원본에 대한 여러 개의 연결을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d667-108">The application can use a combination of drivers and data sources, the same driver and a combination of data sources, or even the same driver and multiple connections to the same data source.</span></span>  
  
 <span data-ttu-id="2d667-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 샘플은 MSDN의 [SQL Server 다운로드](https://go.microsoft.com/fwlink/?LinkId=62796) 페이지에서 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d667-109">You can download [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC samples from the [SQL Server Downloads](https://go.microsoft.com/fwlink/?LinkId=62796) page on MSDN.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2d667-110">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="2d667-110">In This Section</span></span>  
  
-   [<span data-ttu-id="2d667-111">환경 핸들 할당</span><span class="sxs-lookup"><span data-stu-id="2d667-111">Allocating an Environment Handle</span></span>](allocating-an-environment-handle.md)  
  
-   [<span data-ttu-id="2d667-112">연결 핸들 할당</span><span class="sxs-lookup"><span data-stu-id="2d667-112">Allocating a Connection Handle</span></span>](allocating-a-connection-handle.md)  
  
-   [<span data-ttu-id="2d667-113">SQL Server Native Client ODBC 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="2d667-113">SQL Server Native Client ODBC Data Sources</span></span>](../../integration-services/connection-manager/data-sources.md)  
  
-   [<span data-ttu-id="2d667-114">ODBC&#41;&#40;데이터 원본에 연결</span><span class="sxs-lookup"><span data-stu-id="2d667-114">Connecting to a Data Source &#40;ODBC&#41;</span></span>](connecting-to-a-data-source-odbc.md)  
  
-   [<span data-ttu-id="2d667-115">데이터 원본에서 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="2d667-115">Disconnecting from a Data Source</span></span>](disconnecting-from-a-data-source.md)  
  
## <a name="see-also"></a><span data-ttu-id="2d667-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2d667-116">See Also</span></span>  
 <span data-ttu-id="2d667-117">[ODBC&#41;SQL Server Native Client &#40;](../native-client/odbc/sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="2d667-117">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span></span>  
 [<span data-ttu-id="2d667-118">SQLSetEnvAttr</span><span class="sxs-lookup"><span data-stu-id="2d667-118">SQLSetEnvAttr</span></span>](../native-client-odbc-api/sqlsetenvattr.md)  
  
  

---
title: ISO 옵션의 효과 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ISO options (ODBC)
- ODBC applications, ISO options
- ODBC applications, statements
- SQL Server Native Client ODBC driver, ISO options
- statements [ODBC], ISO options
ms.assetid: 813f1397-fa0b-45ec-a718-e13fe2fb88ac
author: rothja
ms.author: jroth
ms.openlocfilehash: 79deff1d77f4020aa7484629bac78d360ed7691f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646409"
---
# <a name="effects-of-iso-options"></a><span data-ttu-id="4217d-102">ISO 옵션의 효과</span><span class="sxs-lookup"><span data-stu-id="4217d-102">Effects of ISO Options</span></span>
  <span data-ttu-id="4217d-103">ODBC 표준은 ISO 표준과 거의 일치하며, ODBC 애플리케이션은 ODBC 드라이버가 표준 동작을 수행할 것으로 예상합니다.</span><span class="sxs-lookup"><span data-stu-id="4217d-103">The ODBC standard is closely matched to the ISO standard, and ODBC applications expect standard behavior from an ODBC driver.</span></span> <span data-ttu-id="4217d-104">Native Client ODBC 드라이버는 해당 동작이 ODBC 표준에 정의 된 것과 더 밀접 하 게 일치 하도록 하기 위해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 항상 연결 하는 SQL Server 버전에서 사용할 수 있는 ISO 옵션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4217d-104">To make its behavior conform more closely with that defined in the ODBC standard, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver always uses any ISO options available in the version of SQL Server with which it connects.</span></span>  
  
 <span data-ttu-id="4217d-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT odbc 드라이버가 인스턴스에 연결할 때 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서버는 클라이언트가 NATIVE client odbc 드라이버를 사용 하 고 있음을 감지 하 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 고 여러 옵션을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4217d-105">When the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver connects to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the server detects that the client is using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver and sets several options on.</span></span>  
  
 <span data-ttu-id="4217d-106">드라이버는 이러한 문을 자체적으로 실행하며 ODBC 애플리케이션에서 이를 요청하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="4217d-106">The driver issues these statements itself; the ODBC application does nothing to request them.</span></span> <span data-ttu-id="4217d-107">이러한 옵션을 설정하면 서버 동작이 ISO 표준과 일치하게 되므로 드라이버를 사용하는 ODBC 애플리케이션의 이식성을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4217d-107">Setting these options allows ODBC applications using the driver to be more portable because the server behavior then matches the ISO standard.</span></span>  
  
 <span data-ttu-id="4217d-108">DB-Library 기반 애플리케이션은 일반적으로 이러한 옵션을 설정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4217d-108">DB-Library-based applications generally do not turn these options on.</span></span> <span data-ttu-id="4217d-109">동일한 SQL 문을 실행할 때 ODBC 또는 DB-LIBRARY 클라이언트 간에 서로 다른 동작을 관찰 하는 사이트는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC 드라이버에 문제가 있다고 가정 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4217d-109">Sites observing different behavior between ODBC or DB-Library clients when running the same SQL statement should not assume this points to a problem with the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="4217d-110">Native Client ODBC 드라이버에서 사용 하는 것과 동일한 SET 옵션을 사용 하 여 DB-LIBRARY 환경에서 문을 먼저 다시 실행 해야 합니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4217d-110">They should first rerun the statement in the DB-Library environment with the same SET options as would be used by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
 <span data-ttu-id="4217d-111">SET 옵션은 사용자와 애플리케이션이 언제라도 설정하거나 해제할 수 있으므로 저장 프로시저 및 트리거 개발자는 위에 나열된 SET 옵션을 설정한 상태와 해제한 상태 모두에서 프로시저 및 트리거를 신중하게 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4217d-111">Because SET options can be turned on and off at any time by users and applications, developers of stored procedures and triggers should also take care to test their procedures and triggers with the SET options listed above turned both on and off.</span></span> <span data-ttu-id="4217d-112">이렇게 하면 프로시저나 트리거가 호출될 때 특정 연결에서 설정하는 옵션에 관계없이 프로시저 및 트리거가 올바르게 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="4217d-112">This ensures that the procedures and triggers work correctly regardless of which options a particular connection may have set on when they invoke the procedure or trigger.</span></span> <span data-ttu-id="4217d-113">위의 옵션 중 하나에 대한 특정한 설정이 필요한 트리거 또는 저장 프로시저는 트리거 또는 저장 프로시저의 시작 부분에서 SET 문을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4217d-113">Triggers or stored procedures that require a particular setting for one of these options should issue a SET statement at the start of the trigger or stored procedure.</span></span> <span data-ttu-id="4217d-114">이 SET 문은 해당 트리거 또는 저장 프로시저가 실행되는 동안에만 적용됩니다. 프로시저 또는 트리거가 종료되면 원래 설정이 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="4217d-114">This SET statement remains in effect only for the execution of the trigger or stored procedure; when the procedure or trigger ends, the original setting is restored.</span></span>  
  
 <span data-ttu-id="4217d-115">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 연결하면 네 번째 SET 옵션인 CONCAT_NULL_YIELDS_NULL이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4217d-115">When connected to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], a fourth SET option, CONCAT_NULL_YIELDS_NULL, is also set on.</span></span> <span data-ttu-id="4217d-116">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]데이터 원본 또는 [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) 또는 [SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md)에 ansinpw = NO가 지정 된 경우 Native Client ODBC 드라이버는 이러한 옵션을 설정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4217d-116">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver does not set these options on if AnsiNPW=NO is specified in the data source or on either [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) or [SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md).</span></span>  
  
 <span data-ttu-id="4217d-117">앞에서 설명한 ISO 옵션과 마찬가지로 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC 드라이버는 QuotedID = NO가 데이터 원본 또는 **SQLDriverConnect** 또는 **SQLBrowseConnect**에 지정 된 경우에는 QUOTED_IDENTIFIER 옵션을 설정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4217d-117">Like the ISO options noted earlier, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver does not turn the QUOTED_IDENTIFIER option on if QuotedID=NO is specified in the data source or on either **SQLDriverConnect** or **SQLBrowseConnect**.</span></span>  
  
 <span data-ttu-id="4217d-118">드라이버가 SET 옵션의 현재 상태를 알 수 있도록 ODBC 애플리케이션은 [!INCLUDE[tsql](../../../includes/tsql-md.md)] SET 문을 사용하여 이러한 옵션을 설정해서는 안 되며</span><span class="sxs-lookup"><span data-stu-id="4217d-118">To allow the driver to know the current state of SET options, ODBC applications should not use the [!INCLUDE[tsql](../../../includes/tsql-md.md)] SET statement to set these options.</span></span> <span data-ttu-id="4217d-119">데이터 원본 또는 연결 옵션을 통해서만 이러한 옵션을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4217d-119">They should only set these options using either the data source or the connection options.</span></span> <span data-ttu-id="4217d-120">애플리케이션이 SET 문을 실행하면 드라이버가 잘못된 SQL 문을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4217d-120">If the application issues SET statements, the driver can generate incorrect SQL statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4217d-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4217d-121">See Also</span></span>  
 <span data-ttu-id="4217d-122">[ODBC&#41;&#40;문을 실행 하는 중](executing-statements-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="4217d-122">[Executing Statements &#40;ODBC&#41;](executing-statements-odbc.md) </span></span>  
 <span data-ttu-id="4217d-123">[SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) </span><span class="sxs-lookup"><span data-stu-id="4217d-123">[SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) </span></span>  
 [<span data-ttu-id="4217d-124">SQLBrowseConnect</span><span class="sxs-lookup"><span data-stu-id="4217d-124">SQLBrowseConnect</span></span>](../../native-client-odbc-api/sqlbrowseconnect.md)  
  
  

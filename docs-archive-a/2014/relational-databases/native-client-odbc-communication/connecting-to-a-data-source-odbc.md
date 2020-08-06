---
title: 데이터 원본에 연결 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- checking connection states
- ODBC data sources, connections
- data sources [SQL Server Native Client]
- SQLBrowseConnect function
- ODBC applications, connections
- ODBC applications, data sources
- connections [SQL Server Native Client]
- SQLConnect function
- SQLDriveConnect function
- verifying connection states
- SQL Server Native Client ODBC driver, data sources
- SQL Server Native Client ODBC driver, connections
ms.assetid: ae30dd1d-06ae-452b-9618-8fd8cd7ba074
author: rothja
ms.author: jroth
ms.openlocfilehash: 25ce5954e45bb8070b5e99d8ebb7bfa9ad149c3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650941"
---
# <a name="connecting-to-a-data-source-odbc"></a><span data-ttu-id="480ee-102">데이터 원본에 연결(ODBC)</span><span class="sxs-lookup"><span data-stu-id="480ee-102">Connecting to a Data Source (ODBC)</span></span>
  <span data-ttu-id="480ee-103">애플리케이션은 환경 및 연결 핸들을 할당하고 연결 특성을 설정한 후 데이터 원본이나 드라이버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-103">After allocating environment and connection handles and setting any connection attributes, the application connects to the data source or driver.</span></span> <span data-ttu-id="480ee-104">연결에 사용할 수 있는 함수는 다음과 같이 세 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-104">There are three functions you can use to connect:</span></span>  
  
-   <span data-ttu-id="480ee-105">**SQLConnect**</span><span class="sxs-lookup"><span data-stu-id="480ee-105">**SQLConnect**</span></span>  
  
-   <span data-ttu-id="480ee-106">**SQLDriverConnect**</span><span class="sxs-lookup"><span data-stu-id="480ee-106">**SQLDriverConnect**</span></span>  
  
-   <span data-ttu-id="480ee-107">**SQLBrowseConnect**</span><span class="sxs-lookup"><span data-stu-id="480ee-107">**SQLBrowseConnect**</span></span>  
  
 <span data-ttu-id="480ee-108">사용할 수 있는 다양 한 연결 문자열 옵션을 포함 하 여 데이터 원본에 연결 하는 방법에 대 한 자세한 내용은 [SQL Server Native Client 연결 문자열 키워드 사용](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="480ee-108">For more information about making connections to a data source, including the various connection string options available, see [Using Connection String Keywords with SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
## <a name="sqlconnect"></a><span data-ttu-id="480ee-109">SQLConnect</span><span class="sxs-lookup"><span data-stu-id="480ee-109">SQLConnect</span></span>  
 <span data-ttu-id="480ee-110">**SQLConnect** 는 가장 간단한 연결 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-110">**SQLConnect** is the simplest connection function.</span></span> <span data-ttu-id="480ee-111">이 함수는 데이터 원본 이름, 사용자 ID 및 암호의 세 가지 매개 변수를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-111">It accepts three parameters: a data source name, a user ID, and a password.</span></span> <span data-ttu-id="480ee-112">이 세 매개 변수에 데이터베이스에 연결 하는 데 필요한 모든 정보가 포함 된 경우 **SQLConnect** 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-112">Use **SQLConnect** when these three parameters contain all the information needed to connect to the database.</span></span> <span data-ttu-id="480ee-113">이렇게 하려면 **sqldatasources**원본을 사용 하 여 데이터 원본 목록을 작성 합니다. 사용자에 게 데이터 원본, 사용자 ID 및 암호를 입력 하 라는 메시지 표시 그런 다음 **SQLConnect**를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-113">To do this, build a list of data sources using **SQLDataSources**; prompt the user for a data source, user ID, and password; and then call **SQLConnect**.</span></span>  
  
 <span data-ttu-id="480ee-114">**SQLConnect** 는 데이터 원본 이름, 사용자 ID 및 암호가 데이터 원본에 연결 하기에 충분 한 것으로 가정 하 고 odbc 드라이버에서 연결을 설정 하는 데 필요한 다른 모든 정보를 odbc 데이터 원본에 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-114">**SQLConnect** assumes that a data source name, user ID, and password are sufficient to connect to a data source and that the ODBC data source contains all other information the ODBC driver needs to make the connection.</span></span> <span data-ttu-id="480ee-115">[SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) 및 [SQLBrowseConnect](../native-client-odbc-api/sqlbrowseconnect.md)와 달리 **SQLConnect** 는 연결 문자열을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-115">Unlike [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) and [SQLBrowseConnect](../native-client-odbc-api/sqlbrowseconnect.md), **SQLConnect** does not use a connection string.</span></span>  
  
## <a name="sqldriverconnect"></a><span data-ttu-id="480ee-116">SQLDriverConnect</span><span class="sxs-lookup"><span data-stu-id="480ee-116">SQLDriverConnect</span></span>  
 <span data-ttu-id="480ee-117">**SQLDriverConnect** 는 데이터 원본 이름, 사용자 ID 및 암호에 대 한 자세한 정보가 필요한 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-117">**SQLDriverConnect** is used when more information than the data source name, user ID, and password is required.</span></span> <span data-ttu-id="480ee-118">**SQLDriverConnect** 에 대 한 매개 변수 중 하나는 드라이버 관련 정보를 포함 하는 연결 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-118">One of the parameters to **SQLDriverConnect** is a connection string containing driver-specific information.</span></span> <span data-ttu-id="480ee-119">다음과 같은 이유로 **SQLConnect** 대신 **SQLDriverConnect** 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-119">You might use **SQLDriverConnect** instead of **SQLConnect** for the following reasons:</span></span>  
  
-   <span data-ttu-id="480ee-120">연결 시 드라이버 관련 정보를 지정하려는 경우</span><span class="sxs-lookup"><span data-stu-id="480ee-120">To specify driver-specific information at connect time.</span></span>  
  
-   <span data-ttu-id="480ee-121">드라이버가 연결 정보를 묻는 메시지를 사용자에게 표시하도록 하려는 경우</span><span class="sxs-lookup"><span data-stu-id="480ee-121">To request that the driver prompt the user for connection information.</span></span>  
  
-   <span data-ttu-id="480ee-122">ODBC 데이터 원본을 사용하지 않고 연결하려는 경우</span><span class="sxs-lookup"><span data-stu-id="480ee-122">To connect without using an ODBC data source.</span></span>  
  
 <span data-ttu-id="480ee-123">**SQLDriverConnect** 연결 문자열에는 ODBC 드라이버에서 지 원하는 모든 연결 정보를 지정 하는 일련의 키워드-값 쌍이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-123">The **SQLDriverConnect** connection string contains a series of keyword-value pairs that specify all connection information supported by an ODBC driver.</span></span> <span data-ttu-id="480ee-124">각 드라이버는 드라이버에서 지원하는 모든 연결 정보에 대해 해당 드라이버의 키워드와 함께 표준 ODBC 키워드(DSN, FILEDSN, DRIVER, UID, PWD 및 SAVEFILE)를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-124">Each driver supports the standard ODBC keywords (DSN, FILEDSN, DRIVER, UID, PWD, and SAVEFILE) in addition to driver-specific keywords for all connection information supported by the driver.</span></span> <span data-ttu-id="480ee-125">**SQLDriverConnect** 는 데이터 원본 없이 연결 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-125">**SQLDriverConnect** can be used to connect without a data source.</span></span> <span data-ttu-id="480ee-126">예를 들어 인스턴스에 "DSN 없음" 연결을 설정 하도록 디자인 된 응용 프로그램은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인 ID, 암호, 네트워크 라이브러리, 연결할 서버 이름 및 사용할 기본 데이터베이스를 정의 하는 연결 문자열을 사용 하 여 **SQLDriverConnect** 를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-126">For example, an application that is designed to make a "DSN-less" connection to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can call **SQLDriverConnect** with a connection string that defines the login ID, password, network library, server name to connect to, and default database to use.</span></span>  
  
 <span data-ttu-id="480ee-127">**SQLDriverConnect**를 사용 하는 경우 사용자에 게 필요한 연결 정보를 요청 하는 두 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-127">When using **SQLDriverConnect**, there are two options for prompting the user for any needed connection information:</span></span>  
  
-   <span data-ttu-id="480ee-128">애플리케이션 대화 상자</span><span class="sxs-lookup"><span data-stu-id="480ee-128">Application dialog box</span></span>  
  
     <span data-ttu-id="480ee-129">연결 정보를 묻는 메시지를 표시 하는 응용 프로그램 대화 상자를 만든 다음 NULL 창 핸들 및 *Drivercompletion* 가 SQL_DRIVER_NOPROMPT로 설정 된 상태에서 **SQLDriverConnect** 를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-129">You can create an application dialog box that prompts for connection information, and then calls **SQLDriverConnect** with a NULL window handle and *DriverCompletion* set to SQL_DRIVER_NOPROMPT.</span></span> <span data-ttu-id="480ee-130">매개 변수를 이렇게 설정하면 ODBC 드라이버가 자체 대화 상자를 열지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-130">These parameter settings prevent the ODBC driver from opening its own dialog box.</span></span> <span data-ttu-id="480ee-131">이 방법은 애플리케이션의 사용자 인터페이스를 제어해야 하는 경우 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-131">This method is used when it is important to control the user interface of the application.</span></span>  
  
-   <span data-ttu-id="480ee-132">드라이버 대화 상자</span><span class="sxs-lookup"><span data-stu-id="480ee-132">Driver dialog box</span></span>  
  
     <span data-ttu-id="480ee-133">응용 프로그램을 코딩 하 여 유효한 창 핸들을 **SQLDriverConnect** 에 전달 하 고 *drivercompletion* 매개 변수를 SQL_DRIVER_COMPLETE, SQL_DRIVER_PROMPT 또는 SQL_DRIVER_COMPLETE_REQUIRED로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-133">You can code the application to pass a valid window handle to **SQLDriverConnect** and set the *DriverCompletion* parameter to SQL_DRIVER_COMPLETE, SQL_DRIVER_PROMPT, or SQL_DRIVER_COMPLETE_REQUIRED.</span></span> <span data-ttu-id="480ee-134">그러면 사용자에게 연결 정보를 묻는 대화 상자를 드라이버에서 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-134">The driver then generates a dialog box to prompt the user for connection information.</span></span> <span data-ttu-id="480ee-135">이 방법을 사용할 경우 애플리케이션 코드가 단순해집니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-135">This method simplifies the application code.</span></span>  
  
## <a name="sqlbrowseconnect"></a><span data-ttu-id="480ee-136">SQLBrowseConnect</span><span class="sxs-lookup"><span data-stu-id="480ee-136">SQLBrowseConnect</span></span>  
 <span data-ttu-id="480ee-137">**SQLDriverConnect**와 같은 **SQLBrowseConnect**는 연결 문자열을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-137">**SQLBrowseConnect**, like **SQLDriverConnect**, uses a connection string.</span></span> <span data-ttu-id="480ee-138">그러나 **SQLBrowseConnect**을 사용 하면 응용 프로그램에서 런타임에 데이터 소스와 함께 반복적으로 전체 연결 문자열을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-138">However, by using **SQLBrowseConnect**, an application can construct a complete connection string iteratively with the data source at run time.</span></span> <span data-ttu-id="480ee-139">이를 통해 애플리케이션에서는 다음 두 가지 작업이 가능해집니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-139">This allows the application to do two things:</span></span>  
  
-   <span data-ttu-id="480ee-140">해당 정보를 묻는 고유의 대화 상자를 만듭니다. 따라서 해당 사용자 인터페이스에 대한 제어를 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-140">Build its own dialog boxes to prompt for this information, thereby retaining control over its user interface.</span></span>  
  
-   <span data-ttu-id="480ee-141">특정 드라이버에서 사용할 수 있는 데이터 원본을 몇 개의 단계에 따라 시스템에서 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-141">Browse the system for data sources that can be used by a particular driver, possibly in several steps.</span></span>  
  
     <span data-ttu-id="480ee-142">예를 들어 사용자는 먼저 네트워크에서 서버를 찾아서 선택한 다음 이 서버에서 드라이버가 액세스할 수 있는 데이터베이스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-142">For example, the user might first browse the network for servers and, after choosing a server, browse the server for databases accessible by the driver.</span></span>  
  
 <span data-ttu-id="480ee-143">**SQLBrowseConnect** 가 성공적으로 연결 되 면 **SQLDriverConnect**에 대 한 후속 호출에서 사용할 수 있는 연결 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-143">When **SQLBrowseConnect** completes a successful connection, it returns a connection string that can be used on subsequent calls to **SQLDriverConnect**.</span></span>  
  
 <span data-ttu-id="480ee-144">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 드라이버는 항상 성공적인 **SQLConnect**, **SQLDriverConnect**또는 **SQLBrowseConnect**에 대 한 SQL_SUCCESS_WITH_INFO를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-144">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver always returns SQL_SUCCESS_WITH_INFO on a successful **SQLConnect**, **SQLDriverConnect**, or **SQLBrowseConnect**.</span></span> <span data-ttu-id="480ee-145">SQL_SUCCESS_WITH_INFO 가져온 후 ODBC 응용 프로그램이 **SQLGetDiagRec** 를 호출 하면 다음과 같은 메시지가 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-145">When an ODBC application calls **SQLGetDiagRec** after getting SQL_SUCCESS_WITH_INFO, it can receive the following messages:</span></span>  
  
 <span data-ttu-id="480ee-146">5701</span><span class="sxs-lookup"><span data-stu-id="480ee-146">5701</span></span>  
 <span data-ttu-id="480ee-147">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 데이터 원본에 정의된 기본 데이터베이스 또는 데이터 원본에 기본 데이터베이스가 없는 경우 연결에 사용된 로그인 ID에 대해 정의된 기본 데이터베이스에 사용자의 컨텍스트를 가져옴을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-147">Indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] put the user's context into the default database defined in the data source, or into the default database defined for the login ID used in the connection if the data source did not have a default database.</span></span>  
  
 <span data-ttu-id="480ee-148">5703</span><span class="sxs-lookup"><span data-stu-id="480ee-148">5703</span></span>  
 <span data-ttu-id="480ee-149">서버에서 사용 중인 언어를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-149">Indicates the language being used on the server.</span></span>  
  
 <span data-ttu-id="480ee-150">다음 예에서는 시스템 관리자가 연결을 성공적으로 수행한 경우 반환되는 메시지를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-150">The following example shows the message returned on a successful connection by the system administrator:</span></span>  
  
```  
szSqlState = "01000", *pfNativeError = 5701,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]  
       Changed database context to 'pubs'."  
szSqlState = "01000", *pfNativeError = 5703,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]  
       Changed language setting to 'us_english'."  
```  
  
 <span data-ttu-id="480ee-151">메시지 5701 및 5703은 정보 메시지일 뿐이므로 무시해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-151">You can ignore messages 5701 and 5703; they are only informational.</span></span> <span data-ttu-id="480ee-152">그러나 5701이나 5703 이외의 메시지가 반환될 수 있으므로 SQL_SUCCESS_WITH_INFO 반환 코드를 주의해서 검토해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-152">You should not, however, ignore a SQL_SUCCESS_WITH_INFO return code because messages other than 5701 or 5703 may be returned.</span></span> <span data-ttu-id="480ee-153">예를 들어 드라이버가 오래 된 카탈로그 저장 프로시저를 사용 하 여 인스턴스를 실행 하는 서버에 연결 하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL_SUCCESS_WITH_INFO 후 **SQLGetDiagRec** 를 통해 반환 되는 오류 중 하나는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-153">For example, if a driver connects to a server running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with outdated catalog stored procedures, one of the errors returned through **SQLGetDiagRec** after a SQL_SUCCESS_WITH_INFO is:</span></span>  
  
```  
SqlState:   01000  
pfNative:   0  
szErrorMsg: "[Microsoft][SQL Server Native Client]The ODBC  
            catalog stored procedures installed on server  
            my65server are version 06.50.0193; version 07.00.0205  
            or later is required to ensure proper operation.  
            Please contact your system administrator."  
```  
  
 <span data-ttu-id="480ee-154">연결에 대 한 응용 프로그램의 오류 처리 함수는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL_NO_DATA 반환 될 때까지 **SQLGetDiagRec** 를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-154">The error handling function of an application for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connections should call **SQLGetDiagRec** until it returns SQL_NO_DATA.</span></span> <span data-ttu-id="480ee-155">그런 다음 *pfNative* 코드가 5701 또는 5703 인 메시지 이외의 모든 메시지에 대해 작업을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="480ee-155">It should then act on any messages other than the ones with a *pfNative* code of 5701 or 5703.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="480ee-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="480ee-156">See Also</span></span>  
 [<span data-ttu-id="480ee-157">SQL Server &#40;ODBC&#41;와 통신</span><span class="sxs-lookup"><span data-stu-id="480ee-157">Communicating with SQL Server &#40;ODBC&#41;</span></span>](communicating-with-sql-server-odbc.md)  
  
  

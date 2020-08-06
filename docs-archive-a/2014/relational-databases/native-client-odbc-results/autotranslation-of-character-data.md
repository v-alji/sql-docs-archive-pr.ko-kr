---
title: 문자 데이터의 자동 변환을 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], autotranslating character data
- data types [ODBC], autotranslating character data
- ACPs
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- AutoTranslate feature
- ANSI code pages
- character data autotranslation [ODBC]
- autotranslating character data
- SQL Server Native Client ODBC driver, data types
- ODBC data types, autotranslating character data
ms.assetid: 86a8adda-c5ad-477f-870f-cb370c39ee13
author: rothja
ms.author: jroth
ms.openlocfilehash: 91dd1714d553f201c1cab78bbca77d2445b42923
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741983"
---
# <a name="autotranslation-of-character-data"></a><span data-ttu-id="3a78c-102">문자 데이터 자동 변환</span><span class="sxs-lookup"><span data-stu-id="3a78c-102">Autotranslation of Character Data</span></span>
  <span data-ttu-id="3a78c-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **CHAR**, **varchar**또는 **text** 데이터 형식을 사용 하 여 SQL_C_CHAR 선언 된 ANSI 문자 변수와 같은 문자 데이터는 제한 된 수의 문자만 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a78c-103">Character data, such as ANSI character variables declared with SQL_C_CHAR or data stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the **char**, **varchar**, or **text** data types, can represent only a limited number of characters.</span></span> <span data-ttu-id="3a78c-104">즉, 문자당 1바이트를 사용하여 저장된 문자 데이터는 246자만 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a78c-104">Character data stored using one byte per character can only represent 256 characters.</span></span> <span data-ttu-id="3a78c-105">SQL_C_CHAR 변수에 저장된 값은 클라이언트 컴퓨터의 ACP(ANSI 코드 페이지)를 사용하여 해석되고,</span><span class="sxs-lookup"><span data-stu-id="3a78c-105">The values stored in SQL_C_CHAR variables are interpreted using the ANSI code page (ACP) of the client computer.</span></span> <span data-ttu-id="3a78c-106">서버에서 **char**, **varchar**또는 **text** 데이터 형식을 사용 하 여 저장 된 값은 서버의 ACP를 사용 하 여 평가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a78c-106">The values stored using **char**, **varchar**, or **text** data types on the server are evaluated using the ACP of the server.</span></span>  
  
 <span data-ttu-id="3a78c-107">서버와 클라이언트 모두에 동일한 ACP가 있는 경우 SQL_C_CHAR, **CHAR**, **varchar**또는 **text** 개체에 저장 된 값을 해석 하는 데 문제가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3a78c-107">If both the server and the client have the same ACP, then they have no problems in interpreting the values stored in SQL_C_CHAR, **char**, **varchar**, or **text** objects.</span></span> <span data-ttu-id="3a78c-108">서버와 클라이언트가 다른 ACPs를 사용 하는 경우 **CHAR**, **varchar**또는 **text** 열, 변수 또는 매개 변수에 사용 되는 경우 클라이언트의 SQL_C_CHAR 데이터가 서버에서 다른 문자로 해석 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a78c-108">If the server and client have different ACPs, then SQL_C_CHAR data from the client may be interpreted as a different character on the server if it is used in **char**, **varchar**, or **text** columns, variables, or parameters.</span></span> <span data-ttu-id="3a78c-109">예를 들어, 0xA5 값을 포함 하는 문자 바이트는 문자?로 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a78c-109">For example, a character byte containing the value 0xA5 is interpreted as the character ??</span></span> <span data-ttu-id="3a78c-110">코드 페이지 437를 사용 하는 컴퓨터에서 코드 페이지 1252를 실행 하는 컴퓨터의 엔화 기호 (??)로 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a78c-110">on a computer using code page 437 and is interpreted as the yen sign (??) on a computer running code page 1252.</span></span>  
  
 <span data-ttu-id="3a78c-111">유니코드 데이터는 문자당 2바이트를 사용하여 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a78c-111">Unicode data is stored using two bytes per character.</span></span> <span data-ttu-id="3a78c-112">유니코드 사양에 따라 모든 확장 문자가 처리되기 때문에 모든 유니코드 문자는 컴퓨터에 관계없이 동일하게 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a78c-112">All extended characters are covered by the Unicode specification, so all Unicode characters are interpreted the same by all computers.</span></span>  
  
 <span data-ttu-id="3a78c-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 드라이버의 자동 변환 기능은 다른 코드 페이지를 포함 하는 클라이언트와 서버 간에 문자 데이터를 이동 하는 문제를 최소화 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a78c-113">The AutoTranslate feature of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver attempts to minimize the problems in moving character data between a client and a server that have different code pages.</span></span> <span data-ttu-id="3a78c-114">AutoTranslate은 [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md)의 연결 문자열에서 설정 하거나, [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)의 구성 문자열에서 설정 하거나, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] odbc 관리자를 사용 하 여 Native Client odbc 드라이버에 대 한 데이터 원본을 구성할 때 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a78c-114">AutoTranslate can be set in the connect string of [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md), in the configuration string of [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md), or when configuring data sources for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver using ODBC Administrator.</span></span>  
  
 <span data-ttu-id="3a78c-115">AutoTranslate를 "no"로 설정 하면 클라이언트의 SQL_C_CHAR 변수와 데이터베이스의 **CHAR**, **varchar**또는 **text** 열, 변수 또는 매개 변수 간에 이동 되는 데이터에 대 한 변환이 수행 되지 않습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3a78c-115">When AutoTranslate is set to "no", no conversions are done on data moved between SQL_C_CHAR variables on the client and **char**, **varchar**, or **text** columns, variables, or parameters in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="3a78c-116">데이터에 확장 문자가 포함되어 있고 클라이언트 컴퓨터와 서버 컴퓨터에서 서로 다른 코드 페이지를 사용하면 두 컴퓨터에서 비트 패턴이 서로 다르게 해석될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a78c-116">The bit patterns may be interpreted differently on the client and server computers if the data contains extended characters and the two computers have different code pages.</span></span> <span data-ttu-id="3a78c-117">그러나 두 컴퓨터에서 동일한 코드 페이지를 사용하면 데이터가 동일하게 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a78c-117">The data will be interpreted the same if both computers have the same code page.</span></span>  
  
 <span data-ttu-id="3a78c-118">AutoTranslate를 "예"로 설정 하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 드라이버는 유니코드를 사용 하 여 클라이언트의 SQL_C_CHAR 변수 사이에서 이동 하는 데이터와 데이터베이스의 **CHAR**, **varchar**또는 **text** 열, 변수 또는 매개 변수로 데이터를 변환 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3a78c-118">When AutoTranslate is set to "yes", the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver uses Unicode to convert data moved between SQL_C_CHAR variables on the client and **char**, **varchar**, or **text** columns, variables, or parameters in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database:</span></span>  
  
-   <span data-ttu-id="3a78c-119">클라이언트의 SQL_C_CHAR 변수에서 데이터베이스의 **CHAR**, **varchar**또는 **text** 열, 변수 또는 매개 변수로 데이터를 전송 하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC 드라이버는 먼저 클라이언트의 Acp를 사용 하 여 SQL_C_CHAR에서 유니코드로 변환한 다음, 서버의 acp를 사용 하 여 유니코드에서 문자로 다시 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a78c-119">When data is sent from an SQL_C_CHAR variable on the client to a **char**, **varchar**, or **text** column, variable, or parameter in an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, the ODBC driver first converts from SQL_C_CHAR to Unicode using the ACP of the client, then from Unicode back to character using the ACP of the server.</span></span>  
  
-   <span data-ttu-id="3a78c-120">데이터베이스의 **char**, **varchar**또는 **text** 열, 변수 또는 매개 변수에서 클라이언트의 SQL_C_CHAR 변수로 데이터가 전송 될 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native client ODBC 드라이버는 먼저 서버 acp를 사용 하 여 문자에서 유니코드로 변환한 다음, 유니코드에서 클라이언트의 acp를 사용 하 여 SQL_C_CHAR으로 다시 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a78c-120">When data is sent from a **char**, **varchar**, or **text** column, variable, or parameter in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database to a SQL_C_CHAR variable on the client, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver first converts from character to Unicode using the ACP of the server, then from Unicode back to SQL_C_CHAR using the ACP of the client.</span></span>  
  
 <span data-ttu-id="3a78c-121">이러한 모든 변환은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 클라이언트에서 실행 되는 Native CLIENT ODBC 드라이버에 의해 수행 되므로 서버 ACP는 클라이언트 컴퓨터에 설치 된 코드 페이지 중 하나 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a78c-121">Because all of these conversions are done by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver executing on the client, the server ACP must be one of the code pages installed on the client computer.</span></span>  
  
 <span data-ttu-id="3a78c-122">유니코드를 통해 문자를 변환하면 두 코드 페이지에 있는 모든 문자가 올바로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a78c-122">Making the character conversions through Unicode ensures the proper conversion of all characters that exist in both code pages.</span></span> <span data-ttu-id="3a78c-123">문자가 한 코드 페이지에만 있고 다른 한 코드 페이지에는 없는 경우 대상 코드 페이지에서 해당 문자를 나타낼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3a78c-123">If a character exists in one code page but not another, however, then the character cannot be represented in the target code page.</span></span> <span data-ttu-id="3a78c-124">예를 들어 코드 페이지 1252는 등록 된 상표 기호 (??)를 포함 하지만 코드 페이지 437는 그렇지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3a78c-124">For example, code page 1252 has the registered trademark symbol (??), while code page 437 does not.</span></span>  
  
 <span data-ttu-id="3a78c-125">다음과 같은 변환 작업은 AutoTranslate 설정의 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3a78c-125">The AutoTranslate setting has no effect on these conversions:</span></span>  
  
-   <span data-ttu-id="3a78c-126">데이터베이스에서 문자 SQL_C_CHAR 클라이언트 변수와 유니코드 **nchar**, **nvarchar**또는 **ntext** 열, 변수 또는 매개 변수로 데이터를 이동 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a78c-126">Moving data between character SQL_C_CHAR client variables and Unicode **nchar**, **nvarchar**, or **ntext** columns, variables, or parameters in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
-   <span data-ttu-id="3a78c-127">데이터베이스에서 유니코드 SQL_C_WCHAR 클라이언트 변수와 문자 **char**, **varchar**또는 **text** 열, 변수 또는 매개 변수 간에 데이터를 이동 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a78c-127">Moving data between Unicode SQL_C_WCHAR client variables and character **char**, **varchar**, or **text** columns, variables, or parameters in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
 <span data-ttu-id="3a78c-128">데이터를 문자에서 유니코드로 이동할 때는 항상 변환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a78c-128">Data always must be converted when moved from character to Unicode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a78c-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3a78c-129">See Also</span></span>  
 <span data-ttu-id="3a78c-130">[ODBC&#41;&#40;결과 처리](processing-results-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="3a78c-130">[Processing Results &#40;ODBC&#41;](processing-results-odbc.md) </span></span>  
 [<span data-ttu-id="3a78c-131">데이터 정렬 및 유니코드 지원</span><span class="sxs-lookup"><span data-stu-id="3a78c-131">Collation and Unicode Support</span></span>](../collations/collation-and-unicode-support.md)  
  
  

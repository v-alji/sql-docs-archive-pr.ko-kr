---
title: 세션 언어 설정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [SQL Server], international considerations
- globalization [SQL Server], sessions
- time [SQL Server]
- sessions [SQL Server], languages
- international considerations [SQL Server], sessions
- dates [SQL Server], session languages
- global considerations [SQL Server], sessions
- client-side session language
- time [SQL Server], session languages
- messages [SQL Server], international considerations
- server-side session language
ms.assetid: de7f2c90-8f4f-4cfc-94cc-4933a7fd2bde
author: stevestein
ms.author: sstein
ms.openlocfilehash: da8d6adce66ac5b97e533b5afaefabda40e4b966
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661168"
---
# <a name="set-a-session-language"></a><span data-ttu-id="39a76-102">세션 언어 설정</span><span class="sxs-lookup"><span data-stu-id="39a76-102">Set a Session Language</span></span>
  <span data-ttu-id="39a76-103">세션 언어를 사용하여 언어 및 문화 기본 설정을 기반으로 다음과 같은 요소가 서버에 표시되는 방식을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39a76-103">The session language can be used to set how the following elements are displayed on the server, based on language and cultural preference:</span></span>  
  
-   <span data-ttu-id="39a76-104">오류 및 기타 시스템 메시지에 사용될 언어입니다.</span><span class="sxs-lookup"><span data-stu-id="39a76-104">The language that will be used for error and other system messages.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="39a76-105">에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 지역화된 모든 언어로 모든 시스템 오류 문자열 및 메시지의 복사본을 여러 개 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39a76-105">supports having multiple copies of all system error strings and messages in all the languages in which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is available.</span></span> <span data-ttu-id="39a76-106">이러한 메시지는 [sys.messages](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages) 카탈로그 뷰를 사용하여 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39a76-106">These messages can be viewed in the [sys.messages](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages) catalog view.</span></span> <span data-ttu-id="39a76-107">해당 언어 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 설치하면 이러한 시스템 메시지가 해당 언어로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="39a76-107">When you install a localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], these system messages are translated for the language version that you install.</span></span> <span data-ttu-id="39a76-108">기본적으로 이러한 메시지의 영어(미국) 집합이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="39a76-108">By default, you also obtain the U.S. English set of these messages.</span></span> <span data-ttu-id="39a76-109">또한 [sp_addmessage](/sql/relational-databases/system-stored-procedures/sp-addmessage-transact-sql)를 사용하여 특정 언어의 사용자 정의 메시지를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39a76-109">Additionally, you can add user-defined messages in a specific language by using [sp_addmessage](/sql/relational-databases/system-stored-procedures/sp-addmessage-transact-sql).</span></span>  
  
-   <span data-ttu-id="39a76-110">날짜 및 시간 데이터의 형식</span><span class="sxs-lookup"><span data-stu-id="39a76-110">The format of date and time data.</span></span>  
  
-   <span data-ttu-id="39a76-111">요일 및 월 이름(약어 포함)</span><span class="sxs-lookup"><span data-stu-id="39a76-111">The names of days and months, including abbreviations.</span></span>  
  
-   <span data-ttu-id="39a76-112">시작 요일</span><span class="sxs-lookup"><span data-stu-id="39a76-112">The first day of the week.</span></span>  
  
-   <span data-ttu-id="39a76-113">통화 데이터</span><span class="sxs-lookup"><span data-stu-id="39a76-113">Currency data.</span></span>  
  
 <span data-ttu-id="39a76-114">33가지의 서로 다른 언어를 세션 설정으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39a76-114">There are 33 languages available for use as session settings.</span></span> <span data-ttu-id="39a76-115">언어 목록을 보려면 [sys.syslanguages](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="39a76-115">For a list of languages, see [sys.syslanguages](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql).</span></span>  
  
## <a name="setting-the-session-language-from-the-server"></a><span data-ttu-id="39a76-116">서버에서 세션 언어 설정</span><span class="sxs-lookup"><span data-stu-id="39a76-116">Setting the Session Language from the Server</span></span>  
 <span data-ttu-id="39a76-117">서버 쪽에서 세션 언어를 설정하려면 [SET LANGUAGE](/sql/t-sql/statements/set-language-transact-sql)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39a76-117">To set the session language from the server side, use [SET LANGUAGE](/sql/t-sql/statements/set-language-transact-sql).</span></span>  
  
## <a name="setting-the-session-language-from-the-client"></a><span data-ttu-id="39a76-118">클라이언트에서 세션 언어 설정</span><span class="sxs-lookup"><span data-stu-id="39a76-118">Setting the Session Language from the Client</span></span>  
 <span data-ttu-id="39a76-119">OLE DB, ODBC 또는 ADO.NET을 사용하여 클라이언트 쪽에서 세션 언어를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39a76-119">The session language can be set on the client side by using OLE DB, ODBC or ADO.NET.</span></span> <span data-ttu-id="39a76-120">OLE DB의 경우 SSPROP_INIT_CURRENTLANGUAGE 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39a76-120">For OLE DB, use the SSPROP_INIT_CURRENTLANGUAGE property.</span></span> <span data-ttu-id="39a76-121">자세한 내용은 [초기화 및 권한 부여 속성](../native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39a76-121">For more information, see [Initialization and Authorization Properties](../native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).</span></span>  
  
 <span data-ttu-id="39a76-122">ODBC의 경우 Language 키워드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39a76-122">For ODBC, use the Language keyword.</span></span> <span data-ttu-id="39a76-123">자세한 내용은 [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39a76-123">For more information, see [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md).</span></span>  
  
 <span data-ttu-id="39a76-124">ADO.NET의 경우 **ConnectionString** 개체의 **Current Language** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39a76-124">For ADO.NET, use the **Current Language** parameter of the **ConnectionString** object.</span></span> <span data-ttu-id="39a76-125">자세한 내용은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] MDAC(데이터 액세스 구성 요소) SDK(소프트웨어 개발 키트) 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="39a76-125">For more information, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Data Access Components (MDAC) software development kit (SDK) documentation.</span></span>  
  
  

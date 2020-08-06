---
title: ODBC 데이터 원본 SQL Server Native Client | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC data sources, about data sources
- ODBC data sources, names
- data sources [SQL Server Native Client]
- names [ODBC]
- ODBC applications, data sources
- SQL Server Native Client ODBC driver, data sources
- ODBC data sources
ms.assetid: a6a50fd0-d439-43fd-b76f-16ec02f478c5
author: rothja
ms.author: jroth
ms.openlocfilehash: 6960118e13f0843640b18056bda655726cbbbd29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650940"
---
# <a name="sql-server-native-client-odbc-data-sources"></a><span data-ttu-id="5e777-102">SQL Server Native Client ODBC 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="5e777-102">SQL Server Native Client ODBC Data Sources</span></span>
  <span data-ttu-id="5e777-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DSN(데이터 원본 이름)은 ODBC 애플리케이션이 특정 서버의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 연결하는 데 필요한 모든 정보가 포함된 ODBC 데이터 원본을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="5e777-103">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data source name (DSN) identifies an ODBC data source containing all of the information that an ODBC application needs to connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database on a specific server.</span></span> <span data-ttu-id="5e777-104">ODBC 데이터 원본 이름은 다음 두 가지 방법으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e777-104">There are two ways you can define an ODBC data source name:</span></span>  
  
-   <span data-ttu-id="5e777-105">클라이언트 컴퓨터의 제어판에서 관리 도구를 열고 **데이터 원본 (ODBC)** 을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e777-105">On a client computer, open Administrative Tools in Control Panel, and double-click **Data Sources (ODBC)**.</span></span> <span data-ttu-id="5e777-106">DSN을 만드는 데 사용하는 ODBC 데이터 원본 관리자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="5e777-106">This will open the ODBC Data Source Administrator, which you can use to create a DSN.</span></span>  
  
-   <span data-ttu-id="5e777-107">ODBC 응용 프로그램에서 [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e777-107">In an ODBC application, call [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md).</span></span>  
  
 <span data-ttu-id="5e777-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 원본에는 다음 항목이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e777-108">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data source contains:</span></span>  
  
-   <span data-ttu-id="5e777-109">데이터 원본의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5e777-109">The name of the data source.</span></span>  
  
-   <span data-ttu-id="5e777-110">특정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결하는 데 필요한 정보</span><span class="sxs-lookup"><span data-stu-id="5e777-110">Any information needed to connect to a specific instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="5e777-111">특정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 사용할 기본 데이터베이스(옵션)</span><span class="sxs-lookup"><span data-stu-id="5e777-111">The default database to use on a specific instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (optional).</span></span>  
  
-   <span data-ttu-id="5e777-112">사용할 ANSI 옵션, 성능 통계 기록 여부 등의 설정(옵션)</span><span class="sxs-lookup"><span data-stu-id="5e777-112">Settings such as which ANSI options to use, whether to log performance statistics, and so on (optional).</span></span>  
  
 <span data-ttu-id="5e777-113">ODBC 애플리케이션이 반드시 데이터 원본을 통해 연결해야 하는 것은 아니지만</span><span class="sxs-lookup"><span data-stu-id="5e777-113">An ODBC application is not required to connect through a data source.</span></span> <span data-ttu-id="5e777-114">이와 같은 연결 정보를 ODBC 연결 함수에 제공해야 합니다. 그렇지 않으면 드라이버가 DSN에서 연결 정보를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5e777-114">However, the application must provide the same connectivity information to an ODBC connect function that the driver would otherwise find in a DSN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e777-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5e777-115">See Also</span></span>  
 [<span data-ttu-id="5e777-116">SQL Server &#40;ODBC&#41;와 통신</span><span class="sxs-lookup"><span data-stu-id="5e777-116">Communicating with SQL Server &#40;ODBC&#41;</span></span>](communicating-with-sql-server-odbc.md)  
  
  

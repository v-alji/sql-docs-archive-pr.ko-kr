---
title: SQL Server Native Client를 사용 하 여 응용 프로그램 빌드 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], building applications
- SQLNCLI, building applications
- applications [SQL Server Native Client]
- SQL Server Native Client, building applications
ms.assetid: 254a2b48-f0e3-43b5-a48d-3d666c2a779f
author: rothja
ms.author: jroth
ms.openlocfilehash: d08fe1042ab1a79f6b48648f5a774b4fbac49ead
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652074"
---
# <a name="building-applications-with-sql-server-native-client"></a><span data-ttu-id="5910d-102">SQL Server Native Client를 사용하여 애플리케이션 빌드</span><span class="sxs-lookup"><span data-stu-id="5910d-102">Building Applications with SQL Server Native Client</span></span>
  <span data-ttu-id="5910d-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 라이브러리를 사용하는 애플리케이션을 개발할 때 발생하는 많은 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5910d-103">When developing an application that uses the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client library, there are a number of issues that come into play.</span></span> <span data-ttu-id="5910d-104">이 섹션의 항목에서는 MDAC에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client로의 업그레이드, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 헤더 및 라이브러리 파일, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client에서 사용할 수 있는 다양한 연결 문자열 개요를 비롯하여 이러한 많은 문제를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5910d-104">The topics in this section discuss many of these issues including upgrading from MDAC to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client header and library files, and an overview of the various connection strings that can be used with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5910d-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="5910d-105">In This Section</span></span>  
 [<span data-ttu-id="5910d-106">SQL Server Native Client 설치</span><span class="sxs-lookup"><span data-stu-id="5910d-106">Installing SQL Server Native Client</span></span>](installing-sql-server-native-client.md)  
 <span data-ttu-id="5910d-107">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 설치 방법, 다양한 구성 요소가 설치되는 위치 및 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 제거 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5910d-107">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client is installed, the locations that various components are installed to, and how to uninstall [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 [<span data-ttu-id="5910d-108">SQL Server Native Client의 구성 요소</span><span class="sxs-lookup"><span data-stu-id="5910d-108">Components of SQL Server Native Client</span></span>](components-of-sql-server-native-client.md)  
 <span data-ttu-id="5910d-109">라이브러리, 리소스, 도움말 및 헤더 파일을 비롯하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client를 구성하는 구성 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5910d-109">Discusses the components that make up [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client including library, resource, help, and header files.</span></span>  
  
 [<span data-ttu-id="5910d-110">SQL Server Native Client에서 연결 문자열 키워드 사용</span><span class="sxs-lookup"><span data-stu-id="5910d-110">Using Connection String Keywords with SQL Server Native Client</span></span>](using-connection-string-keywords-with-sql-server-native-client.md)  
 <span data-ttu-id="5910d-111">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client를 통해 데이터베이스에 연결할 때 사용할 수 있는 다양한 연결 문자열 유형에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5910d-111">Discusses the various types of connection strings that can be used when connecting to a database through [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 [<span data-ttu-id="5910d-112">SQL Server Native Client 헤더 및 라이브러리 파일 사용</span><span class="sxs-lookup"><span data-stu-id="5910d-112">Using the SQL Server Native Client Header and Library Files</span></span>](using-the-sql-server-native-client-header-and-library-files.md)  
 <span data-ttu-id="5910d-113">애플리케이션 내에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 헤더 및 라이브러리 파일을 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5910d-113">Discusses how to use the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client header and library files within an application.</span></span>  
  
 [<span data-ttu-id="5910d-114">MDAC에서 SQL Server Native Client로 애플리케이션 업데이트</span><span class="sxs-lookup"><span data-stu-id="5910d-114">Updating an Application to SQL Server Native Client from MDAC</span></span>](updating-an-application-to-sql-server-native-client-from-mdac.md)  
 <span data-ttu-id="5910d-115">MDAC에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client로 업그레이드할 때 고려해야 하는 문제 및 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client와 MDAC의 차이점에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5910d-115">Discusses the differences between [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client and MDAC and issues that should be considered when upgrading from MDAC to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 [<span data-ttu-id="5910d-116">SQL Server 2005 Native Client에서 응용 프로그램 업데이트</span><span class="sxs-lookup"><span data-stu-id="5910d-116">Updating an Application from SQL Server 2005 Native Client</span></span>](updating-an-application-from-sql-server-2005-native-client.md)  
 <span data-ttu-id="5910d-117">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Native Client에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client로 업그레이드할 때 고려해야 하는 문제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5910d-117">Discusses issues that should be considered when upgrading from [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Native Client to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].</span></span>  
  
 [<span data-ttu-id="5910d-118">SQL Server Native Client와 함께 ADO 사용</span><span class="sxs-lookup"><span data-stu-id="5910d-118">Using ADO with SQL Server Native Client</span></span>](using-ado-with-sql-server-native-client.md)  
 <span data-ttu-id="5910d-119">ADO에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client를 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 기능에 액세스하고 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5910d-119">Discusses how ADO can use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client to access and use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] functionality.</span></span>  
  
 [<span data-ttu-id="5910d-120">SQL Server Native Client에 대한 지원 정책</span><span class="sxs-lookup"><span data-stu-id="5910d-120">Support Policies for SQL Server Native Client</span></span>](support-policies-for-sql-server-native-client.md)  
 <span data-ttu-id="5910d-121">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client의 여러 버전에서 다양한 데이터 액세스 구성 요소를 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5910d-121">Discusses how various data-access components can be used with different versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 [<span data-ttu-id="5910d-122">SQL Server Native Client를 사용하여 Azure SQL Database에 연결</span><span class="sxs-lookup"><span data-stu-id="5910d-122">Connecting to an Azure SQL Database Using SQL Server Native Client</span></span>](connecting-to-a-windows-azure-sql-database-using-sql-server-native-client.md)  
 <span data-ttu-id="5910d-123">[!INCLUDE[ssSDS](../../../includes/sssds-md.md)] Native Client를 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 연결하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5910d-123">Discusses how to connect to a [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5910d-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5910d-124">See Also</span></span>  
 <span data-ttu-id="5910d-125">[SQL Server Native Client 프로그래밍](../sql-server-native-client-programming.md) </span><span class="sxs-lookup"><span data-stu-id="5910d-125">[SQL Server Native Client Programming](../sql-server-native-client-programming.md) </span></span>  
 <span data-ttu-id="5910d-126">[ODBC 방법 도움말 항목](../../native-client-odbc-how-to/odbc-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="5910d-126">[ODBC How-to Topics](../../native-client-odbc-how-to/odbc-how-to-topics.md) </span></span>  
 [<span data-ttu-id="5910d-127">OLE DB 방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="5910d-127">OLE DB How-to Topics</span></span>](../../native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  

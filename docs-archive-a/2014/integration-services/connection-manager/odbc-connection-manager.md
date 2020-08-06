---
title: ODBC 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], ODBC
- ODBC connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], ODBC
ms.assetid: e8c77aa7-6772-485e-918e-cef9eeb18c58
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e1069e31f3f8ffaf14dde091d913ff6d9f8fa7cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649628"
---
# <a name="odbc-connection-manager"></a><span data-ttu-id="82bf2-102">ODBC 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="82bf2-102">ODBC Connection Manager</span></span>
  <span data-ttu-id="82bf2-103">ODBC 연결 관리자를 사용하면 패키지에서 ODBC(Open Database Connectivity) 사양을 사용하여 다양한 데이터베이스 관리 시스템에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82bf2-103">An ODBC connection manager enables a package to connect to a variety of database management systems using the Open Database Connectivity specification (ODBC).</span></span>  
  
 <span data-ttu-id="82bf2-104">패키지에 ODBC 연결을 추가 하 고 연결 관리자 속성을 설정할 때는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 연결 관리자를 만들고 패키지의 컬렉션에 연결 관리자를 추가 합니다 `Connections` .</span><span class="sxs-lookup"><span data-stu-id="82bf2-104">When you add an ODBC connection to a package and set the connection manager properties, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager and adds the connection manager to the `Connections` collection of the package.</span></span> <span data-ttu-id="82bf2-105">런타임 시 연결 관리자는 물리적 ODBC 연결로 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="82bf2-105">At run time the connection manager is resolved as a physical ODBC connection.</span></span>  
  
 <span data-ttu-id="82bf2-106">연결 관리자의 `ConnectionManagerType` 속성이 `ODBC`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="82bf2-106">The `ConnectionManagerType` property of the connection manager is set to `ODBC`.</span></span>  
  
 <span data-ttu-id="82bf2-107">다음과 같은 방법으로 ODBC 연결 관리자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82bf2-107">You can configure the ODBC connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="82bf2-108">사용자 또는 시스템 데이터 원본 이름을 참조하는 연결 문자열을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="82bf2-108">Provide a connection string that references a user or system data source name.</span></span>  
  
-   <span data-ttu-id="82bf2-109">연결할 서버를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="82bf2-109">Specify the server to connect to.</span></span>  
  
-   <span data-ttu-id="82bf2-110">런타임 시 연결이 유지되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="82bf2-110">Indicate whether the connection is retained at run time.</span></span>  
  
## <a name="configuration-of-the-odbc-connection-manager"></a><span data-ttu-id="82bf2-111">ODBC 연결 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="82bf2-111">Configuration of the ODBC Connection Manager</span></span>  
 <span data-ttu-id="82bf2-112">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82bf2-112">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="82bf2-113">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="82bf2-113">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topic:</span></span>  
  
-   [<span data-ttu-id="82bf2-114">ODBC 연결 관리자 UI 참조</span><span class="sxs-lookup"><span data-stu-id="82bf2-114">ODBC Connection Manager UI Reference</span></span>](../odbc-connection-manager-ui-reference.md)  
  
 <span data-ttu-id="82bf2-115">연결 관리자를 프로그래밍 방식으로 구성하는 방법에 대한 자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 및 [프로그래밍 방식으로 연결 추가](../building-packages-programmatically/adding-connections-programmatically.md)로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="82bf2-115">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82bf2-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="82bf2-116">See Also</span></span>  
 [<span data-ttu-id="82bf2-117">Integration Services&#40;SSIS&#41; 연결</span><span class="sxs-lookup"><span data-stu-id="82bf2-117">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  

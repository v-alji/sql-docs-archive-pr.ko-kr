---
title: SQL Server Compact Edition 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Compact, connection manager
- connections [Integration Services], SQL Server Compact
- connection managers [Integration Services], SQL Server Compact
ms.assetid: ba627d4d-41f4-49fc-a921-f534cde67770
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5d4feb001cc7c0fd0bd8b6e60d5ab22b33ad2eb9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741187"
---
# <a name="sql-server-compact-edition-connection-manager"></a><span data-ttu-id="8407d-102">SQL Server Compact Edition 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="8407d-102">SQL Server Compact Edition Connection Manager</span></span>
  <span data-ttu-id="8407d-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 연결 관리자를 사용하면 패키지에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 데이터베이스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8407d-103">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact connection manager enables a package to connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact database.</span></span> <span data-ttu-id="8407d-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 포함된 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Compact 대상은 이 연결 관리자를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 데이터베이스의 테이블에 데이터를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="8407d-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes uses this connection manager to load data into a table in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8407d-105">64비트 컴퓨터에서는 32비트 모드로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 데이터 원본에 연결하는 패키지를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8407d-105">On a 64-bit computer, you must run packages that connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact data sources in 32-bit mode.</span></span> <span data-ttu-id="8407d-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Compact 데이터 원본에 연결할 때 사용하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 공급자는 32비트 버전에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8407d-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact provider that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] uses to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact data sources is available only in a 32-bit version.</span></span>  
  
## <a name="configuration-the-sql-server-compact-edition-connection-manager"></a><span data-ttu-id="8407d-107">SQL Server Compact Edition 연결 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="8407d-107">Configuration the SQL Server Compact Edition Connection Manager</span></span>  
 <span data-ttu-id="8407d-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]패키지에 compact 연결 관리자를 추가 하면에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 런타임에 compact 연결로 확인 되는 연결 관리자를 만들고, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 연결 관리자 속성을 설정 하 고, 연결 관리자를 `Connections` 패키지의 컬렉션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8407d-108">When you add a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span>  
  
 <span data-ttu-id="8407d-109">연결 관리자의 `ConnectionManagerType` 속성이 `SQLMOBILE`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8407d-109">The `ConnectionManagerType` property of the connection manager is set to `SQLMOBILE`.</span></span>  
  
 <span data-ttu-id="8407d-110">다음과 같은 방법으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 연결 관리자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8407d-110">You can configure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="8407d-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 데이터베이스의 위치를 지정하는 연결 문자열을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8407d-111">Provide a connection string that specifies the location of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
-   <span data-ttu-id="8407d-112">암호로 보호되는 데이터베이스에 대한 암호를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8407d-112">Provide a password for a password-protected database.</span></span>  
  
-   <span data-ttu-id="8407d-113">데이터베이스가 저장된 서버를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8407d-113">Specify the server on which the database is stored.</span></span>  
  
-   <span data-ttu-id="8407d-114">연결 관리자에서 만든 연결이 런타임에 유지될지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8407d-114">Indicate whether the connection that is created from the connection manager is retained at run time.</span></span>  
  
 <span data-ttu-id="8407d-115">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8407d-115">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="8407d-116">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="8407d-116">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="8407d-117">SQL Server Compact Edition 연결 관리자 편집기&#40;연결 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="8407d-117">SQL Server Compact Edition Connection Manager Editor &#40;Connection Page&#41;</span></span>](../sql-server-compact-edition-connection-manager-editor-connection-page.md)  
  
-   [<span data-ttu-id="8407d-118">SQL Server Compact Edition 연결 관리자 편집기&#40;모든 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="8407d-118">SQL Server Compact Edition Connection Manager Editor &#40;All Page&#41;</span></span>](../sql-server-compact-edition-connection-manager-editor-all-page.md)  
  
 <span data-ttu-id="8407d-119">연결 관리자를 프로그래밍 방식으로 구성하는 방법에 대한 자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 및 [프로그래밍 방식으로 연결 추가](../building-packages-programmatically/adding-connections-programmatically.md)로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8407d-119">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
  

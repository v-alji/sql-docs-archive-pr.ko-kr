---
title: SQL Server 연결 CDC Service에 필요한 권한 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: d9e968f9-180c-4fa0-a849-98f2b1942330
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e63b98ffd0371bd5b70ecc0ac843ad40a4a5d03e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649632"
---
# <a name="sql-server-connection-required-permissions-for-the-cdc-service"></a><span data-ttu-id="5b781-102">SQL Server 연결 CDC Service에 필요한 권한</span><span class="sxs-lookup"><span data-stu-id="5b781-102">SQL Server Connection Required Permissions for the CDC Service</span></span>
  <span data-ttu-id="5b781-103">CDC Service 구성 콘솔에서 태스크를 수행하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 연결 정보가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5b781-103">The CDC Service Configuration Console requires connection information to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to perform their tasks.</span></span> <span data-ttu-id="5b781-104">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]연결 설정을 위해 SQL Server에 연결 대화 상자에서 지정할 수 있는 정보에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5b781-104">This topic describes the information that can be provided in the Connect to SQL Server dialog box for setting up the connection to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="5b781-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 연결 정보를 사용할 수 없거나 정보가 있지만 연결에 필요한 권한이 없는 경우와 같이 필요한 경우 SQL Server에 연결 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="5b781-105">The Connect to SQL Server dialog box opens when necessary, such as when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection information is not available or when the information exists but the connection does not have the required permissions.</span></span>  
  
 <span data-ttu-id="5b781-106">다음 표에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 연결이 필요한 다양한 태스크와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인/사용자의 필요한 권한에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5b781-106">The following table describes the various tasks where a connection to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is required and the required permissions from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login/user.</span></span>  
  
|<span data-ttu-id="5b781-107">Task</span><span class="sxs-lookup"><span data-stu-id="5b781-107">Task</span></span>|<span data-ttu-id="5b781-108">최소 권한</span><span class="sxs-lookup"><span data-stu-id="5b781-108">Minimum Permissions</span></span>|  
|----------|-------------------------|  
|<span data-ttu-id="5b781-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="5b781-109">Prepare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instance.</span></span>|<span data-ttu-id="5b781-110">`dbcreator` 고정 서버 역할</span><span class="sxs-lookup"><span data-stu-id="5b781-110">`dbcreator` fixed-server role</span></span>|  
|<span data-ttu-id="5b781-111">Oracle CDC Service에서 사용할 Oracle CDC Service-SQL Server 로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5b781-111">Create an Oracle CDC Service-SQL Server login for use by the Oracle CDC service.</span></span>|<span data-ttu-id="5b781-112">`public` 고정 서버 역할</span><span class="sxs-lookup"><span data-stu-id="5b781-112">`public` fixed-server role</span></span>|  
|<span data-ttu-id="5b781-113">MSXDBCDC에서 새 서비스를 등록하는 데 사용할 Oracle CDC Service-로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5b781-113">Create an Oracle CDC Service-login to use for registering the new service in MSXDBCDC.</span></span>|<span data-ttu-id="5b781-114">`db_datareader` 및 `db_datawriter` 역할</span><span class="sxs-lookup"><span data-stu-id="5b781-114">`db_datareader` and `db_datawriter` roles on MSXDBCDC</span></span>|  
|<span data-ttu-id="5b781-115">MSXDBCDC에서 서비스의 등록을 업데이트하는 데 사용할 Oracle CDC Service-로그인을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="5b781-115">Edit an Oracle CDC Service-login to use for updating the registration of the service in MSXDBCDC.</span></span>|<span data-ttu-id="5b781-116">`db_datareader` 및 `db_datawriter` 역할</span><span class="sxs-lookup"><span data-stu-id="5b781-116">`db_datareader` and `db_datawriter` roles on MSXDBCDC</span></span>|  
|<span data-ttu-id="5b781-117">MSXDBCDC에서 서비스의 등록을 업데이트하는 데 사용할 Oracle CDC Service-로그인을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="5b781-117">Delete an Oracle CDC Service-login to use for updating the registration of the service in MSXDBCDC.</span></span>|<span data-ttu-id="5b781-118">`db_datareader` 및 `db_datawriter` 역할</span><span class="sxs-lookup"><span data-stu-id="5b781-118">`db_datareader` and `db_datawriter` roles on MSXDBCDC</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5b781-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5b781-119">See Also</span></span>  
 <span data-ttu-id="5b781-120">[SQL 서버에 연결](connection-to-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5b781-120">[Connection to SQL Server](connection-to-sql-server.md) </span></span>  
 [<span data-ttu-id="5b781-121">삭제를 위해 SQL Server에 연결</span><span class="sxs-lookup"><span data-stu-id="5b781-121">Connection to SQL Server for Delete</span></span>](connection-to-sql-server-for-delete.md)  
  
  

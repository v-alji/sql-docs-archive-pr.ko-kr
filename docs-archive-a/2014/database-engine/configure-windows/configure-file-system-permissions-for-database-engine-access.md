---
title: 데이터베이스 엔진 액세스에 대한 파일 시스템 권한 구성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- file system permissions
- service account [SQL Server], file system permissions
- permissions [SQL Server], file system
ms.assetid: 78bba43c-4edb-4216-84ac-d6246ae5546d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1d9abbd095f2d5be7415ed28a17fb710ff8ab504
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661360"
---
# <a name="configure-file-system-permissions-for-database-engine-access"></a><span data-ttu-id="349fc-102">데이터베이스 엔진 액세스에 대한 파일 시스템 사용 권한 구성</span><span class="sxs-lookup"><span data-stu-id="349fc-102">Configure File System Permissions for Database Engine Access</span></span>
  <span data-ttu-id="349fc-103">이 항목에서는 데이터베이스 파일이 저장된 위치에 파일 시스템 즉, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]에 대한 액세스 권한을 부여하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="349fc-103">This topic describes how to grant the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], file system access to the location where database files are stored.</span></span> <span data-ttu-id="349fc-104">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 서비스를 사용하려면 Windows 파일 시스템에서 데이터베이스 파일이 저장된 파일 폴더에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="349fc-104">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] service must have permission of the Windows file system to access the file folder where database files are stored.</span></span> <span data-ttu-id="349fc-105">기본 위치에 대한 사용 권한은 설치 중에 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="349fc-105">Permission to the default location is configured during setup.</span></span> <span data-ttu-id="349fc-106">데이터베이스 파일을 다른 위치에 저장한 경우 다음 단계를 수행하여 해당 위치에 대한 모든 권한을 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에 부여해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="349fc-106">If you place your database files in a different location, you might need to follow these steps to grant the [!INCLUDE[ssDE](../../includes/ssde-md.md)] the full control permission to that location.</span></span>  
  
 <span data-ttu-id="349fc-107">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 사용 권한부터 각 서비스에 대해 서비스별 SID에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="349fc-107">Beginning with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] permissions are assigned to the per-service SID for each of its services.</span></span> <span data-ttu-id="349fc-108">이 시스템에서는 서비스 격리 및 철저한 방어 기능을 제공하도록 돕습니다.</span><span class="sxs-lookup"><span data-stu-id="349fc-108">This system helps provide service isolation and defense in depth.</span></span> <span data-ttu-id="349fc-109">서비스별 SID는 서비스 이름에서 파생되며 각 서비스마다 고유합니다.</span><span class="sxs-lookup"><span data-stu-id="349fc-109">The per-service SID is derived from the service name and is unique to each service.</span></span> <span data-ttu-id="349fc-110">[Windows 서비스 계정 및 사용 권한 구성](configure-windows-service-accounts-and-permissions.md) 항목에서는 서비스별 SID에 대해 설명하며 **Windows 권한 및 권리**섹션에 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="349fc-110">The topic [Configure Windows Service Accounts and Permissions](configure-windows-service-accounts-and-permissions.md) describes the per-service SID and provides the names in the section **Windows Privileges and Rights**.</span></span> <span data-ttu-id="349fc-111">파일 위치에 대한 액세스 권한을 할당해야 하는 서비스별 SID입니다.</span><span class="sxs-lookup"><span data-stu-id="349fc-111">It is the per-service SID that must be assigned the access permission on the file location.</span></span>  
  
## <a name="to-grant-file-system-permission-to-the-per-service-sid"></a><span data-ttu-id="349fc-112">서비스별 SID에 파일 시스템 권한을 부여하려면</span><span class="sxs-lookup"><span data-stu-id="349fc-112">To Grant File System Permission to the Per-service SID</span></span>  
  
1.  <span data-ttu-id="349fc-113">Windows 탐색기를 사용하여 데이터베이스 파일이 저장된 파일 시스템 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="349fc-113">Using Windows Explorer, navigate to the file system location where the database files are stored.</span></span> <span data-ttu-id="349fc-114">파일 시스템 폴더를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="349fc-114">Right-click the file system folder, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="349fc-115">**보안** 탭에서 **편집**을 클릭한 다음 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="349fc-115">On the **Security** tab, click **Edit**, and then **Add**.</span></span>  
  
3.  <span data-ttu-id="349fc-116">**사용자, 컴퓨터, 서비스 계정 또는 그룹 선택** 대화 상자에서 위치 목록 맨 위에 있는 **위치**를 클릭하고 컴퓨터 이름을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="349fc-116">In the **Select Users, Computer, Service Account, or Groups** dialog box, click **Locations**, at the top of the location list, select your computer name, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="349fc-117">**선택할 개체 이름을 입력 하십시오** . 상자에 온라인 설명서 항목 **Windows 서비스 계정 및 권한 구성**에 나열 된 서비스별 SID의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="349fc-117">In the **Enter the object names to select** box, type the name of the per-service SID listed in the Books Online topic **Configure Windows Service Accounts and Permissions**.</span></span> <span data-ttu-id="349fc-118">( [!INCLUDE[ssDE](../../includes/ssde-md.md)] 서비스 당 SID의 경우 기본 인스턴스에 대해 **nt SERVICE\MSSQLSERVER** 를 사용 하 고 명명 된 인스턴스에 대해 **nt service\ssql $ InstanceName** 을 사용 합니다.)</span><span class="sxs-lookup"><span data-stu-id="349fc-118">(For the [!INCLUDE[ssDE](../../includes/ssde-md.md)] per service SID, use **NT SERVICE\MSSQLSERVER** for a default instance, or **NT SERVICE\MSSQL$InstanceName** for a named instance.)</span></span>  
  
5.  <span data-ttu-id="349fc-119">**이름 확인** 을 클릭하여 항목의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="349fc-119">Click **Check Names** to validate the entry.</span></span> <span data-ttu-id="349fc-120">유효성 검사가 종종 실패하며 이름을 찾을 수 없음이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="349fc-120">The validation often fails, and might advise you that the name was not found.</span></span> <span data-ttu-id="349fc-121">**확인**을 클릭하면 **여러 이름 찾음** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="349fc-121">When you click **OK**, a **Multiple Names Found** dialog box appears.</span></span>  
  
6.  <span data-ttu-id="349fc-122">이제 **MSSQLSERVER** 또는 **NT service\ssql $ INSTANCENAME**의 서비스별 SID를 선택 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="349fc-122">Now select the per-service SID, either **MSSQLSERVER** or **NT SERVICE\MSSQL$InstanceName**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="349fc-123">**확인** 을 다시 클릭 하 여 **사용 권한** 대화 상자로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="349fc-123">Click **OK** again to return to the **Permissions** dialog box.</span></span>  
  
8.  <span data-ttu-id="349fc-124">**그룹 또는 사용자** 이름 상자에서 서비스별 SID를 선택한 다음 **에 대 한 사용 권한** \<name> 상자에서 **모든**권한에 대해 **허용** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="349fc-124">In the **Group or user** names box, select the per-service SID, and then in the **Permissions for** \<name> box, select the **Allow** check box for **Full control**.</span></span>  
  
9. <span data-ttu-id="349fc-125">**적용**을 클릭한 다음 **확인** 을 두 번 클릭하여 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="349fc-125">Click **Apply**, and then click **OK** twice to exit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="349fc-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="349fc-126">See Also</span></span>  
 <span data-ttu-id="349fc-127">[데이터베이스 엔진 서비스 관리](manage-the-database-engine-services.md) </span><span class="sxs-lookup"><span data-stu-id="349fc-127">[Manage the Database Engine Services](manage-the-database-engine-services.md) </span></span>  
 <span data-ttu-id="349fc-128">[시스템 데이터베이스 이동](../../relational-databases/databases/system-databases.md) </span><span class="sxs-lookup"><span data-stu-id="349fc-128">[Move System Databases](../../relational-databases/databases/system-databases.md) </span></span>  
 [<span data-ttu-id="349fc-129">사용자 데이터베이스 이동</span><span class="sxs-lookup"><span data-stu-id="349fc-129">Move User Databases</span></span>](../../relational-databases/databases/move-user-databases.md)  
  
  

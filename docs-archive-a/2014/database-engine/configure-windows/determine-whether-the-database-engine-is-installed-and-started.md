---
title: 데이터베이스 엔진이 설치 및 시작되었는지 확인 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server, determining if installed
- verifying Database Engine installation
- viewing Database Engine installation
- installed Database Engine verification [SQL Server]
ms.assetid: babb02e4-3521-4b75-b5df-e09205594375
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0a912cf4a89f208543605cc84f480b63955214ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740419"
---
# <a name="determine-whether-the-database-engine-is-installed-and-started"></a><span data-ttu-id="cf923-102">데이터베이스 엔진이 설치 및 시작되었는지 확인</span><span class="sxs-lookup"><span data-stu-id="cf923-102">Determine Whether the Database Engine Is Installed and Started</span></span>
  <span data-ttu-id="cf923-103">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 설치에 성공하면 파일 시스템에 파일이 설치되고 레지스트리에 항목이 생성되며 여러 가지 도구가 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf923-103">A successful installation of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] installs files to the file system, creates entries in the registry, and installs several tools.</span></span> <span data-ttu-id="cf923-104">이 항목에서는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 구성 관리자를 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이 설치 및 시작되었는지 여부를 확인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cf923-104">This topic describes how to determine whether the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is installed and started in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cf923-105">SQL Server 구성 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="cf923-105">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="how-to-view-and-start-the-database-engine-by-using-sql-server-configuration-manager"></a><span data-ttu-id="cf923-106">SQL Server 구성 관리자를 사용하여 데이터베이스 엔진을 보고 시작하는 방법</span><span class="sxs-lookup"><span data-stu-id="cf923-106">How to view and start the Database Engine by using SQL Server Configuration Manager</span></span>  
  
1.  <span data-ttu-id="cf923-107">**시작**을 클릭하고 **모든 프로그램**, **Microsoft SQL Server**, **구성 도구**를 차례로 가리킨 다음 **SQL Server 구성 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf923-107">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
     <span data-ttu-id="cf923-108">**시작** 메뉴에 이러한 항목이 없으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 올바르게 설치되지 않은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cf923-108">If you do not have these entries on the **Start** menu, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not correctly installed.</span></span> <span data-ttu-id="cf923-109">설치 프로그램을 실행하여 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="cf923-109">Run Setup to install the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="cf923-110">**SQL Server 구성 관리자**의 왼쪽 창에서 **SQL Server 서비스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf923-110">In **SQL Server Configuration Manager**, on the left pane, click **SQL Server Services**.</span></span> <span data-ttu-id="cf923-111">오른쪽 창에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 관련된 여러 가지 서비스가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf923-111">The right pane lists several services that are related to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="cf923-112">[!INCLUDE[ssDE](../../includes/ssde-md.md)]이 설치되어 있으면 기본 인스턴스인 경우 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 서비스가 **SQL Server(MSSQLSERVER)** 로 표시되고, [!INCLUDE[ssDE](../../includes/ssde-md.md)]이 명명된 인스턴스로 설치된 경우 **SQL Server(** \<*instance_name*> **)** 로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf923-112">If the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is installed, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] service is listed as **SQL Server (MSSQLSERVER)** if it is the default instance; or **SQL Server (**\<*instance_name*>**)**, if the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is installed as a named instance.</span></span> <span data-ttu-id="cf923-113">인스턴스 이름을 변경하지 않으면 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 는 **SQLEXPRESS**라는 이름의 명명된 인스턴스로 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf923-113">Unless the instance name is changed, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installs as a named instance with the name **SQLEXPRESS**.</span></span> <span data-ttu-id="cf923-114">녹색 삼각형 아이콘은 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 이 실행되고 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cf923-114">A green triangle icon indicates that the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is running.</span></span> <span data-ttu-id="cf923-115">빨간색 정사각형 아이콘은 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 이 중지되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cf923-115">A red square icon indicates that the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is stopped.</span></span>  
  
3.  <span data-ttu-id="cf923-116">[!INCLUDE[ssDE](../../includes/ssde-md.md)]을 시작하려면 오른쪽 창에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]을 마우스 오른쪽 단추로 클릭한 다음 **시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf923-116">To start the [!INCLUDE[ssDE](../../includes/ssde-md.md)], in the right pane, right-click the [!INCLUDE[ssDE](../../includes/ssde-md.md)], and then click **Start**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cf923-117">설치 중에 사용자는 프로그램 파일과 데이터베이스 파일을 설치할 위치를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf923-117">During setup, the user can select a location in which to install the program files and the database files.</span></span> <span data-ttu-id="cf923-118">사용자가 기본 위치를 적용하면 파일은 [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)] 및 C:\Program Files\Microsoft SQL Server\MSSQL.*x*에 설치됩니다. 여기서 *x* 는 숫자입니다.</span><span class="sxs-lookup"><span data-stu-id="cf923-118">If the user accepts the default location, the files are installed to [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)] and C:\Program Files\Microsoft SQL Server\MSSQL.*x*, where *x* is a number.</span></span>  
  
  

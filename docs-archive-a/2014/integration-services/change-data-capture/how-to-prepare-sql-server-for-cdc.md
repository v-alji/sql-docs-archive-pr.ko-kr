---
title: CDC를 위해 SQL Server를 준비하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a327fa18-58f4-4e69-bb87-44faf47e20ef
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fbd285faaa55a28ad82beb673fa783570809bd04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727307"
---
# <a name="how-to-prepare-sql-server-for-cdc"></a><span data-ttu-id="061b1-102">CDC를 위해 SQL Server를 준비하는 방법</span><span class="sxs-lookup"><span data-stu-id="061b1-102">How to Prepare SQL Server for CDC</span></span>
  <span data-ttu-id="061b1-103">Oracle CDC Service에서는 모든 대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 MSXDBCDC 데이터베이스가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="061b1-103">The Oracle CDC service requires all target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances to contain the MSXDBCDC database.</span></span> <span data-ttu-id="061b1-104">CDC Service 구성 콘솔에서 SQL Server 준비 동작을 사용하여 이 데이터베이스를 만듭니다. 이 태스크는 각 대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대해 한 번만 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="061b1-104">You create this database using the Prepare SQL Server action in the CDC Service Configuration Console.This task is done one time only for each target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="061b1-105">다음에서는 CDC Service 구성 콘솔을 사용하여 Oracle Change Data Capture를 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스를 준비하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="061b1-105">The following describes how to prepare a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database for Oracle Change Data Capture using the CDC Service Configuration Console.</span></span> <span data-ttu-id="061b1-106">이 프로세스는 MSXDBCDC 데이터베이스를 만들고 필수 테이블, 저장 프로시저 및 기타 필수 아티팩트를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="061b1-106">This process creates the MSXDBCDC database and defines the required tables, stored procedures, and other required artifacts.</span></span>  
  
 <span data-ttu-id="061b1-107">Oracle CDC를 위해 SQL Server를 준비하는 작업은 Oracle CDC Service 관리자가 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="061b1-107">Preparing the SQL Server for Oracle CDC is done by the Oracle CDC Service Administrator.</span></span> <span data-ttu-id="061b1-108">CDC Service 관리자 역할에 대 한 자세한 내용은 [사용자 역할의 Change Data Capture Service for Oracle에 대 한 사용자 역할](user-roles.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="061b1-108">For more information about the CDC Service Administrator role, see [User Roles for Change Data Capture Service for Oracle by Attunity](user-roles.md).</span></span>  
  
### <a name="to-enable-sql-server-for-cdc"></a><span data-ttu-id="061b1-109">CDC용 SQL Server를 활성화하려면</span><span class="sxs-lookup"><span data-stu-id="061b1-109">To enable SQL Server for CDC</span></span>  
  
1.  <span data-ttu-id="061b1-110">**시작** 메뉴에서 **Oracle CDC Service 구성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="061b1-110">From the **Start** menu, select the **CDC Service Configuration for Oracle**.</span></span>  
  
2.  <span data-ttu-id="061b1-111">왼쪽 창에서 **로컬 CDC Service** 를 선택한 다음 **작업** 창에서 **SQL Server 준비**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="061b1-111">From the left pane, select **Local CDC Services** then from the **Actions** pane, click **Prepare SQL Server**.</span></span>  
  
     <span data-ttu-id="061b1-112">**로컬 CDC Service** 를 마우스 오른쪽 단추로 클릭하고 **SQL Server 준비**를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="061b1-112">You can also right-click **Local CDC Services** and select **Prepare SQL Server**.</span></span>  
  
3.  <span data-ttu-id="061b1-113">Oracle CDC를 위한 SQL Server 인스턴스 준비 대화 상자에 필요한 정보를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="061b1-113">Enter the required information in the Preparing SQL Server Instance for Oracle CDC dialog box.</span></span> <span data-ttu-id="061b1-114">이 대화 상자에 필요한 정보를 입력하는 방법은 [Prepare SQL Server for CDC](prepare-sql-server-for-cdc.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="061b1-114">For information on how to enter the required information into this dialog box, see [Prepare SQL Server for CDC](prepare-sql-server-for-cdc.md).</span></span>  
  
     <span data-ttu-id="061b1-115">Oracle CDC를 위해 SQL Server 인스턴스를 준비하려면 로그인은 MSXDBCDC 데이터베이스에 대해 쓰기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="061b1-115">To Prepare the SQL Server instance for Oracle CDC, the login must have write permission to the MSXDBCDC database.</span></span> <span data-ttu-id="061b1-116">MSXDBCDC 데이터베이스에 대해 쓰기 권한이 있는 로그인(예: `sysasmin` 역할의 멤버)의 자격 증명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="061b1-116">Enter the credentials for a login that has write permission to the MSXDBCDC database, such as a member of the `sysasmin` role.</span></span>  
  
 <span data-ttu-id="061b1-117">**참고**: **스크립트 보기** 를 클릭하여 설치 스크립트의 읽기 전용 버전을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="061b1-117">**Note**: You can click **View Script** to view a read-only version of the setup script.</span></span> <span data-ttu-id="061b1-118">필요한 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템 관리자는 이 스크립트를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 관리 콘솔에 복사하여 편집하고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="061b1-118">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator can copy this script into the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Console to edit and execute it, if necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="061b1-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="061b1-119">See Also</span></span>  
 [<span data-ttu-id="061b1-120">CDC를 위한 SQL Server 준비</span><span class="sxs-lookup"><span data-stu-id="061b1-120">Prepare SQL Server for CDC</span></span>](prepare-sql-server-for-cdc.md)  
  
  

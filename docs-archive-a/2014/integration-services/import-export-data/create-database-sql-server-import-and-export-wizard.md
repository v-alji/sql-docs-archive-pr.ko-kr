---
title: 데이터베이스 만들기(SQL Server 가져오기 및 내보내기 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.createdatabase.f1
ms.assetid: 56a8a79f-086c-4bdc-8888-0045bb4b0cbf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 617b3fe10a17ae2d8659b51e85cdb3fed4470506
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652933"
---
# <a name="create-database-sql-server-import-and-export-wizard"></a><span data-ttu-id="c185c-102">데이터베이스 만들기(SQL Server 가져오기 및 내보내기 마법사)</span><span class="sxs-lookup"><span data-stu-id="c185c-102">Create Database (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="c185c-103">**데이터베이스 만들기** 페이지를 사용하여 대상 파일에 대한 새 데이터베이스를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c185c-103">Use the **Create Database** page to define a new database for a destination file.</span></span>  
  
 <span data-ttu-id="c185c-104">이 페이지에서는 새 데이터베이스 생성에 사용할 수 있는 옵션의 하위 집합을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c185c-104">This page offers a subset of the available options for creating a new database.</span></span> <span data-ttu-id="c185c-105">모든 옵션을 보려면를 사용 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="c185c-105">To view all the options, use [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="c185c-106">이 마법사에 대해 자세히 알아보려면 [SQL Server 가져오기 및 내보내기 마법사](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c185c-106">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="c185c-107">마법사 시작 옵션 및 마법사를 성공적으로 실행 하는 데 필요한 권한에 대 한 자세한 내용은 [SQL Server 가져오기 및 내보내기 마법사 실행](start-the-sql-server-import-and-export-wizard.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c185c-107">To learn about the options for starting the wizard, and about the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="c185c-108">SQL Server 가져오기 및 내보내기 마법사의 목적은 원본에서 대상으로 데이터를 복사하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c185c-108">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="c185c-109">이 마법사는 대상 데이터베이스 및 대상 테이블도 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c185c-109">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="c185c-110">그러나 여러 개의 데이터베이스 또는 테이블을 복사하거나 다른 종류의 데이터베이스 개체를 복사할 경우 대신 데이터베이스 복사 마법사를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c185c-110">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="c185c-111">자세한 내용은 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c185c-111">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="c185c-112">옵션</span><span class="sxs-lookup"><span data-stu-id="c185c-112">Options</span></span>  
 <span data-ttu-id="c185c-113">**이름**</span><span class="sxs-lookup"><span data-stu-id="c185c-113">**Name**</span></span>  
 <span data-ttu-id="c185c-114">대상 SQL Server 데이터베이스에 사용할 고유 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c185c-114">Provide a unique name for the destination SQL Server database.</span></span> <span data-ttu-id="c185c-115">SQL Server 규칙에 따라 이 데이터베이스의 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c185c-115">Make sure that you follow SQL Server conventions when you name this database.</span></span>  
  
 <span data-ttu-id="c185c-116">**데이터 파일 이름**</span><span class="sxs-lookup"><span data-stu-id="c185c-116">**Data file name**</span></span>  
 <span data-ttu-id="c185c-117">데이터 파일의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c185c-117">View the name of the data file.</span></span> <span data-ttu-id="c185c-118">데이터 파일의 이름은 앞에서 제공한 데이터베이스 이름에서 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="c185c-118">This is derived from the database name you provided earlier.</span></span>  
  
 <span data-ttu-id="c185c-119">**로그 파일 이름**</span><span class="sxs-lookup"><span data-stu-id="c185c-119">**Log file name**</span></span>  
 <span data-ttu-id="c185c-120">로그 파일의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c185c-120">View the name of the log file.</span></span> <span data-ttu-id="c185c-121">데이터 파일의 이름은 앞에서 제공한 데이터베이스 이름에서 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="c185c-121">This is derived from the database name you provided earlier.</span></span>  
  
 <span data-ttu-id="c185c-122">**처음 크기(데이터 파일)**</span><span class="sxs-lookup"><span data-stu-id="c185c-122">**Initial size (data file)**</span></span>  
 <span data-ttu-id="c185c-123">데이터 파일의 처음 크기(MB)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c185c-123">Specify the number of megabytes for the initial size of the data file.</span></span>  
  
 <span data-ttu-id="c185c-124">**증가 허용 안 함(데이터 파일)**</span><span class="sxs-lookup"><span data-stu-id="c185c-124">**No growth allowed (data file)**</span></span>  
 <span data-ttu-id="c185c-125">데이터 파일이 지정한 처음 크기 이상으로 증가할 수 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c185c-125">Indicate whether the data file can grow beyond the specified initial size.</span></span>  
  
 <span data-ttu-id="c185c-126">**백분율 단위로 증가(데이터 파일)**</span><span class="sxs-lookup"><span data-stu-id="c185c-126">**Grow by percentage (data file)**</span></span>  
 <span data-ttu-id="c185c-127">데이터 파일의 증가 단위(백분율)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c185c-127">Specify a percentage by which the data file can grow.</span></span>  
  
 <span data-ttu-id="c185c-128">**크기 단위로 증가(데이터 파일)**</span><span class="sxs-lookup"><span data-stu-id="c185c-128">**Grow by size (data file)**</span></span>  
 <span data-ttu-id="c185c-129">데이터 파일의 증가 단위(MB)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c185c-129">Specify a number of megabytes by which the data file can grow.</span></span>  
  
 <span data-ttu-id="c185c-130">**처음 크기(로그 파일)**</span><span class="sxs-lookup"><span data-stu-id="c185c-130">**Initial size (log file)**</span></span>  
 <span data-ttu-id="c185c-131">로그 파일의 처음 크기(MB)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c185c-131">Specify the number of megabytes for the initial size of the log file.</span></span>  
  
 <span data-ttu-id="c185c-132">**증가 허용 안 함(로그 파일)**</span><span class="sxs-lookup"><span data-stu-id="c185c-132">**No growth allowed (log file)**</span></span>  
 <span data-ttu-id="c185c-133">로그 파일이 지정한 처음 크기 이상으로 증가할 수 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c185c-133">Indicate whether the log file can grow beyond the specified initial size.</span></span>  
  
 <span data-ttu-id="c185c-134">**백분율 단위로 증가(로그 파일)**</span><span class="sxs-lookup"><span data-stu-id="c185c-134">**Grow by percentage (log file)**</span></span>  
 <span data-ttu-id="c185c-135">로그 파일의 증가 단위(백분율)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c185c-135">Specify a percentage by which the log file can grow.</span></span>  
  
 <span data-ttu-id="c185c-136">**크기 단위로 증가(로그 파일)**</span><span class="sxs-lookup"><span data-stu-id="c185c-136">**Grow by size (log file)**</span></span>  
 <span data-ttu-id="c185c-137">로그 파일의 증가 단위(MB)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c185c-137">Specify a number of megabytes by which the log file can grow.</span></span>  
  
  

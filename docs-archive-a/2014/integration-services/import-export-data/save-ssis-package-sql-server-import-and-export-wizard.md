---
title: SSIS 패키지 저장(SQL Server 가져오기 및 내보내기 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.savedtspackage.f1
ms.assetid: 7bf8ac6a-5599-43ab-bf5c-e072c11b85a0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d4e582558a1f86b18d935fcc6235ba5839faa031
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652916"
---
# <a name="save-ssis-package-sql-server-import-and-export-wizard"></a><span data-ttu-id="bfb4e-102">SSIS 패키지 저장(SQL Server 가져오기 및 내보내기 마법사)</span><span class="sxs-lookup"><span data-stu-id="bfb4e-102">Save SSIS Package (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="bfb4e-103">**SSIS 패키지 저장** 페이지를 사용 하 여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` 데이터베이스 또는 확장명이 package.dtsx 인 파일에 Integration Services () 패키지를 이름, 설명 및 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-103">Use the **Save SSIS Package** page to name, describe, and save a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Integration Services ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) package to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` database or to a file that has the .dtsx extension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bfb4e-104">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]에서는 마법사가 만든 패키지를 저장하는 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-104">In [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], the option to save the package created by the wizard is not available.</span></span>  
  
 <span data-ttu-id="bfb4e-105">이 마법사에 대해 자세히 알아보려면 [SQL Server 가져오기 및 내보내기 마법사](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-105">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="bfb4e-106">마법사 시작 옵션 및 마법사를 성공적으로 실행 하는 데 필요한 권한에 대 한 자세한 내용은 [SQL Server 가져오기 및 내보내기 마법사 실행](start-the-sql-server-import-and-export-wizard.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-106">To learn about the options for starting the wizard, and about the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="bfb4e-107">SQL Server 가져오기 및 내보내기 마법사의 목적은 원본에서 대상으로 데이터를 복사하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-107">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="bfb4e-108">이 마법사는 대상 데이터베이스 및 대상 테이블도 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-108">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="bfb4e-109">그러나 여러 개의 데이터베이스 또는 테이블을 복사하거나 다른 종류의 데이터베이스 개체를 복사할 경우 대신 데이터베이스 복사 마법사를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-109">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="bfb4e-110">자세한 내용은 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-110">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="bfb4e-111">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="bfb4e-111">Static Options</span></span>  
 <span data-ttu-id="bfb4e-112">**이름**</span><span class="sxs-lookup"><span data-stu-id="bfb4e-112">**Name**</span></span>  
 <span data-ttu-id="bfb4e-113">패키지에 사용할 고유 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-113">Provide a unique name for the package.</span></span>  
  
 <span data-ttu-id="bfb4e-114">**설명**</span><span class="sxs-lookup"><span data-stu-id="bfb4e-114">**Description**</span></span>  
 <span data-ttu-id="bfb4e-115">패키지에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-115">Provide a description for the package.</span></span> <span data-ttu-id="bfb4e-116">해당 패키지의 용도를 설명하여 패키지를 이해하기 쉽고 유지 관리하기 편하도록 만드는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-116">As a best practice, describe the package in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="bfb4e-117">**대상**</span><span class="sxs-lookup"><span data-stu-id="bfb4e-117">**Target**</span></span>  
 <span data-ttu-id="bfb4e-118">대상 파일에 대해 이전에 지정된 대상([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 파일)을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-118">View the target ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or file) that was previously specified for the destination file.</span></span>  
  
## <a name="target-dynamic-options"></a><span data-ttu-id="bfb4e-119">대상 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="bfb4e-119">Target Dynamic Options</span></span>  
  
### <a name="target--sql-server"></a><span data-ttu-id="bfb4e-120">대상 = SQL Server</span><span class="sxs-lookup"><span data-stu-id="bfb4e-120">Target = SQL Server</span></span>  
 <span data-ttu-id="bfb4e-121">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="bfb4e-121">**Server name**</span></span>  
 <span data-ttu-id="bfb4e-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 대상을 선택한 경우 대상 서버 이름을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-122">When you have selected a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, type or select the destination server name.</span></span>  
  
 <span data-ttu-id="bfb4e-123">**Windows 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="bfb4e-123">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="bfb4e-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 대상을 선택한 경우 Windows 통합 인증을 사용하여 서버에 연결할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-124">When you have selected a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, specify whether to connect to the server by using Windows Integrated Authentication.</span></span> <span data-ttu-id="bfb4e-125">이 방법은 기본적으로 사용되는 인증 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-125">This is the preferred authentication method.</span></span>  
  
 <span data-ttu-id="bfb4e-126">**SQL Server 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="bfb4e-126">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="bfb4e-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 대상을 선택한 경우 SQL Server 인증을 사용하여 서버에 연결할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-127">When you have selected a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, specify whether to connect to the server by using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="bfb4e-128">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="bfb4e-128">**User name**</span></span>  
 <span data-ttu-id="bfb4e-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 대상을 선택하고 SQL Server 인증을 지정한 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-129">When you have selected a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, and have specified SQL Server Authentication, type the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user name.</span></span>  
  
 <span data-ttu-id="bfb4e-130">**암호**</span><span class="sxs-lookup"><span data-stu-id="bfb4e-130">**Password**</span></span>  
 <span data-ttu-id="bfb4e-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 대상을 선택하고 SQL Server 인증을 지정한 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-131">When you have selected a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, and have specified SQL Server Authentication, type the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] password.</span></span>  
  
### <a name="target--file-system"></a><span data-ttu-id="bfb4e-132">대상 = 파일 시스템</span><span class="sxs-lookup"><span data-stu-id="bfb4e-132">Target = File System</span></span>  
 <span data-ttu-id="bfb4e-133">**파일 이름**</span><span class="sxs-lookup"><span data-stu-id="bfb4e-133">**File name**</span></span>  
 <span data-ttu-id="bfb4e-134">파일 대상을 선택한 경우 대상 파일의 경로를 입력하거나 **찾아보기** 단추를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-134">When you have selected a file destination, type the path for the destination file, or use the **Browse** button.</span></span>  
  
 <span data-ttu-id="bfb4e-135">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="bfb4e-135">**Browse**</span></span>  
 <span data-ttu-id="bfb4e-136">파일 대상을 선택한 경우 **패키지 저장** 대화 상자를 사용하여 대상 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-136">When you have selected a file destination, browse to the destination file by using the **Save Package** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfb4e-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bfb4e-137">See Also</span></span>  
 [<span data-ttu-id="bfb4e-138">패키지 저장</span><span class="sxs-lookup"><span data-stu-id="bfb4e-138">Save Packages</span></span>](../save-packages.md)  
  
  

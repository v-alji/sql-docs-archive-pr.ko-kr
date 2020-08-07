---
title: 의미 체계 검색 설치 및 구성 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], installing
- semantic search [SQL Server], configuring
ms.assetid: 2cdd0568-7799-474b-82fb-65d79df3057c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8d95e0bb2adf3bacf7057b881ab2e85afd50feef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733792"
---
# <a name="install-and-configure-semantic-search"></a><span data-ttu-id="b6beb-102">의미 체계 검색 설치 및 구성</span><span class="sxs-lookup"><span data-stu-id="b6beb-102">Install and Configure Semantic Search</span></span>
  <span data-ttu-id="b6beb-103">통계 의미 체계 검색을 위한 필수 구성 요소와 이러한 필수 구성 요소의 설치 또는 확인 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-103">Describes the prerequisites for statistical semantic search and how to install or check them.</span></span>  
  
## <a name="installing-semantic-search"></a><span data-ttu-id="b6beb-104">의미 체계 검색 설치</span><span class="sxs-lookup"><span data-stu-id="b6beb-104">Installing Semantic Search</span></span>  
  
###  <a name="how-to-check-whether-semantic-search-is-installed"></a><a name="HowToCheckInstalled"></a><span data-ttu-id="b6beb-105">방법: 의미 체계 검색이 설치 되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="b6beb-105">How To: Check Whether Semantic Search Is Installed</span></span>  
 <span data-ttu-id="b6beb-106">[SERVERPROPERTY&#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) 메타데이터 함수의 **IsFullTextInstalled** 속성을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-106">Query the **IsFullTextInstalled** property of the [SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) metadata function.</span></span>  
  
 <span data-ttu-id="b6beb-107">반환 값이 1이면 전체 텍스트 검색과 의미 체계 검색이 설치되어 있음을 나타내고, 반환 값이 0이면 그렇지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-107">A return value of 1 indicates that Full-Text Search and Semantic Search are installed; a return value of 0 indicates that they are not installed.</span></span>  
  
```sql  
SELECT SERVERPROPERTY('IsFullTextInstalled');  
GO  
```  
  
###  <a name="how-to-install-semantic-search"></a><a name="BasicsSemanticSearch"></a><span data-ttu-id="b6beb-108">방법: 의미 체계 검색 설치</span><span class="sxs-lookup"><span data-stu-id="b6beb-108">How To: Install Semantic Search</span></span>  
 <span data-ttu-id="b6beb-109">의미 체계 검색을 설치하려면 설치 중에 **설치할 기능** 페이지에서 **검색을 위한 전체 텍스트 및 의미 체계 추출**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-109">To install Semantic Search, select **Full-Text and Semantic Extractions for Search** on the **Features to Install** page during setup.</span></span>  
  
 <span data-ttu-id="b6beb-110">통계 의미 체계 검색은 전체 텍스트 검색을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-110">Statistical Semantic Search depends on Full-Text Search.</span></span> <span data-ttu-id="b6beb-111">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 이 두 가지 선택적 기능이 함께 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-111">These two optional features of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] are installed together.</span></span>  
  
## <a name="installing-or-removing-the-semantic-language-statistics-database"></a><span data-ttu-id="b6beb-112">의미 체계 언어 통계 데이터베이스 설치 또는 제거</span><span class="sxs-lookup"><span data-stu-id="b6beb-112">Installing or Removing the Semantic Language Statistics Database</span></span>  
 <span data-ttu-id="b6beb-113">의미 체계 검색에는 의미 체계 언어 통계 데이터베이스라고 하는 추가적인 외부 종속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-113">Semantic Search has an additional external dependency that is called the semantic language statistics database.</span></span> <span data-ttu-id="b6beb-114">이 데이터베이스는 의미 체계 검색에 필요한 통계적 언어 모델을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-114">This database contains the statistical language models required by semantic search.</span></span> <span data-ttu-id="b6beb-115">단일 의미 체계 언어 통계 데이터베이스에는 의미 체계 인덱싱에 지원되는 모든 언어에 대한 언어 모델이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-115">A single semantic language statistics database contains the language models for all the languages that are supported for semantic indexing.</span></span>  
  
###  <a name="how-to-check-whether-the-semantic-language-statistics-database-is-installed"></a><a name="HowToCheckDatabase"></a><span data-ttu-id="b6beb-116">방법: 의미 체계 언어 통계 데이터베이스가 설치 되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="b6beb-116">How To: Check Whether the Semantic Language Statistics Database Is Installed</span></span>  
 <span data-ttu-id="b6beb-117">카탈로그 뷰 [sys.fulltext_semantic_language_statistics_database&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql)를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-117">Query the catalog view [sys.fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql).</span></span>  
  
 <span data-ttu-id="b6beb-118">인스턴스에 대해 의미 체계 언어 통계 데이터베이스를 설치하여 등록한 경우 쿼리 결과에 데이터베이스에 대한 단일 정보 행이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-118">If the semantic language statistics database is installed and registered for the instance, then the query results contain a single row of information about the database.</span></span>  
  
```vb  
SELECT * FROM sys.fulltext_semantic_language_statistics_database;  
GO  
```  
  
###  <a name="how-to-install-attach-and-register-the-semantic-language-statistics-database"></a><a name="HowToInstallModel"></a><span data-ttu-id="b6beb-119">방법: 의미 체계 언어 통계 데이터베이스 설치, 연결 및 등록</span><span class="sxs-lookup"><span data-stu-id="b6beb-119">How To: Install, Attach, and Register the Semantic Language Statistics Database</span></span>  
 <span data-ttu-id="b6beb-120">의미 체계 언어 통계 데이터베이스는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 설치 프로그램을 통해 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-120">The semantic language statistics database is not installed by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] setup program.</span></span> <span data-ttu-id="b6beb-121">의미 체계 언어 통계 데이터베이스를 의미 체계 인덱싱을 위한 필수 구성 요소로 설정하려면 다음 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-121">To set up the Semantic Language Statistics database as a prerequisite for semantic indexing, do the following tasks:</span></span>  
  
 <span data-ttu-id="b6beb-122">**1. 의미 체계 언어 통계 데이터베이스를 설치합니다.**</span><span class="sxs-lookup"><span data-stu-id="b6beb-122">**1. Install the semantic language statistics database.**</span></span>  
 1.  <span data-ttu-id="b6beb-123">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 설치 미디어에서 의미 체계 언어 통계 데이터베이스를 찾거나 웹에서 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-123">Locate the semantic language statistics database on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation media or download it from the Web.</span></span>  
  
    -   <span data-ttu-id="b6beb-124">**설치 미디어에서** SemanticLanguageDatabase.msi [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 라는 Windows Installer 패키지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-124">Locate the Windows installer package named **SemanticLanguageDatabase.msi** on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation media.</span></span> <span data-ttu-id="b6beb-125">대상 시스템에 따라 32비트 또는 64비트 버전의 설치 관리자 패키지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-125">Locate the 32-bit or 64-bit version of the installer package depending on the target system.</span></span> <span data-ttu-id="b6beb-126">포함된 폴더의 이름으로 파일의 32비트 버전과 64비트 버전을 식별하며, 파일 이름은 두 버전 모두 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-126">The name of the containing folder identifies the 32-bit or 64-bit version of the file; the file name itself is the same for both versions.</span></span>  
  
    -   <span data-ttu-id="b6beb-127">Microsoft?에서 설치 관리자 패키지를 다운로드 합니다. [ SQL Server?? 2014](https://go.microsoft.com/fwlink/?LinkID=296743) 다운로드 센터의 의미 체계 언어 통계 페이지 [!INCLUDE[msCoName](../../../includes/msconame-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6beb-127">Download the installer package from the [Microsoft?? SQL Server?? 2014 Semantic Language Statistics](https://go.microsoft.com/fwlink/?LinkID=296743) page on the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Download Center.</span></span>  
  
2.  <span data-ttu-id="b6beb-128">**SemanticLanguageDatabase.msi** Windows installer 패키지를 실행 하 여 데이터베이스 및 로그 파일을 추출 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-128">Run the **SemanticLanguageDatabase.msi** Windows installer package to extract the database and log file.</span></span>  
  
     <span data-ttu-id="b6beb-129">필요에 따라 대상 디렉터리를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-129">You can optionally change the destination directory.</span></span> <span data-ttu-id="b6beb-130">기본적으로 설치 관리자는 32 비트 또는 64 비트 Program Files 폴더에 있는 **Microsoft 의미 체계 언어 데이터베이스** 라는 폴더에 파일을 추출 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-130">By default, the installer extracts the files to a folder named **Microsoft Semantic Language Database** in the 32-bit or 64-bit Program Files folder.</span></span> <span data-ttu-id="b6beb-131">MSI 파일에는 압축된 데이터베이스 파일 및 로그 파일이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-131">The MSI file contains a compressed database file and log file.</span></span>  
  
3.  <span data-ttu-id="b6beb-132">추출한 데이터베이스 파일 및 로그 파일을 파일 시스템의 적절한 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-132">Move the extracted database file and log file to a suitable location in the file system.</span></span>  
  
     <span data-ttu-id="b6beb-133">이러한 파일을 기본 위치에 그대로 둘 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 다른 인스턴스를 위해 또 다른 데이터베이스 복사본을 추출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-133">If you leave the files in their default location, it will not be possible to extract another copy of the database for another instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b6beb-134">의미 체계 언어 통계 데이터베이스를 추출할 때 파일 시스템의 기본 위치에 있는 데이터베이스 파일 및 로그 파일에 제한된 사용 권한이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-134">When the semantic language statistics database is extracted, restricted permissions are assigned to the database file and log file in the default location in the file system.</span></span> <span data-ttu-id="b6beb-135">따라서 이 파일을 기본 위치에 그대로 둘 경우 데이터베이스에 연결할 수 있는 권한이 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-135">As a result, you may not have permission to attach the database if you leave it in the default location.</span></span> <span data-ttu-id="b6beb-136">데이터베이스를 연결하려고 할 때 오류가 발생하는 경우 파일을 이동하거나 파일 시스템 사용 권한이 적절한지 확인하여 수정하세요.</span><span class="sxs-lookup"><span data-stu-id="b6beb-136">If an error is raised when you try to attach the database, move the files, or check and fix file system permissions as appropriate.</span></span>  
  
 <span data-ttu-id="b6beb-137">**2. 의미 체계 언어 통계 데이터베이스를 연결합니다.**</span><span class="sxs-lookup"><span data-stu-id="b6beb-137">**2. Attach the semantic language statistics database.**</span></span>  
 <span data-ttu-id="b6beb-138">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]를 사용하거나 **FOR ATTACH** 구문으로 [CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)를 호출하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 데이터베이스를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-138">Attach the database to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] or by calling [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) with the **FOR ATTACH** syntax.</span></span> <span data-ttu-id="b6beb-139">자세한 내용은 [데이터베이스 분리 및 연결&#40;SQL Server&#41;](../databases/database-detach-and-attach-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b6beb-139">For more information, see [Database Detach and Attach &#40;SQL Server&#41;](../databases/database-detach-and-attach-sql-server.md).</span></span>  
  
 <span data-ttu-id="b6beb-140">기본적으로 데이터베이스 이름은 **이름은 semanticsdb**입니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-140">By default, the name of the database is **semanticsdb**.</span></span> <span data-ttu-id="b6beb-141">필요에 따라 데이터베이스를 연결할 때 데이터베이스에 다른 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-141">You can optionally give the database a different name when you attach it.</span></span> <span data-ttu-id="b6beb-142">이후 단계에서 데이터베이스를 등록할 때 이 이름을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-142">You have to provide this name when you register the database in the subsequent step.</span></span>  
  
```sql  
CREATE DATABASE semanticsdb  
            ON ( FILENAME = 'C:\Microsoft Semantic Language Database\semanticsdb.mdf' )  
            LOG ON ( FILENAME = 'C:\Microsoft Semantic Language Database\semanticsdb_log.ldf' )  
            FOR ATTACH;  
GO  
```  
  
 <span data-ttu-id="b6beb-143">이 코드 예제에서는 데이터베이스를 기본 위치에서 새 위치로 이동했다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-143">This code sample assumes that you have moved the database from its default location to a new location.</span></span>  
  
 <span data-ttu-id="b6beb-144">**3. 의미 체계 언어 통계 데이터베이스 등록**</span><span class="sxs-lookup"><span data-stu-id="b6beb-144">**3. Register the semantic language statistics database.**</span></span>  
 <span data-ttu-id="b6beb-145">저장 프로시저 [sp_fulltext_semantic_register_language_statistics_db&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-register-language-statistics-db-transact-sql)를 호출하고 연결 시 데이터베이스에 지정한 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-145">Call the stored procedure [sp_fulltext_semantic_register_language_statistics_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-register-language-statistics-db-transact-sql) and provide the name that you gave to the database when you attached it.</span></span>  
  
```sql  
EXEC sp_fulltext_semantic_register_language_statistics_db @dbname = N'semanticsdb';  
GO  
```  
  
###  <a name="how-to-unregister-detach-and-remove-the-semantic-language-statistics-database"></a><a name="HowToUnregister"></a><span data-ttu-id="b6beb-146">방법: 의미 체계 언어 통계 데이터베이스 등록 취소, 분리 및 제거</span><span class="sxs-lookup"><span data-stu-id="b6beb-146">How To: Unregister, Detach, and Remove the Semantic Language Statistics Database</span></span>  
 <span data-ttu-id="b6beb-147">**의미 체계 언어 통계 데이터베이스의 등록을 취소 합니다.**</span><span class="sxs-lookup"><span data-stu-id="b6beb-147">**Unregister the semantic language statistics database.**</span></span>  
 <span data-ttu-id="b6beb-148">저장 프로시저 [sp_fulltext_semantic_unregister_language_statistics_db&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-unregister-language-statistics-db-transact-sql)를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-148">Call the stored procedure [sp_fulltext_semantic_unregister_language_statistics_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-unregister-language-statistics-db-transact-sql).</span></span> <span data-ttu-id="b6beb-149">인스턴스는 의미 체계 언어 통계 데이터베이스를 하나만 가질 수 있으므로 데이터베이스의 이름을 제공할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-149">You do not have to provide the name of the database since an instance can have only one semantic language statistics database.</span></span>  
  
```sql  
EXEC sp_fulltext_semantic_unregister_language_statistics_db;  
GO  
```  
  
 <span data-ttu-id="b6beb-150">**의미 체계 언어 통계 데이터베이스를 분리 합니다.**</span><span class="sxs-lookup"><span data-stu-id="b6beb-150">**Detach the semantic language statistics database.**</span></span>  
 <span data-ttu-id="b6beb-151">저장 프로시저 [sp_detach_db&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql)를 호출하고 데이터베이스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-151">Call the stored procedure [sp_detach_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql) and provide the name of the database.</span></span>  
  
```sql  
USE master;  
GO  
  
EXEC sp_detach_db @dbname = N'semanticsdb';  
GO  
```  
  
 <span data-ttu-id="b6beb-152">**의미 체계 언어 통계 데이터베이스를 제거 합니다.**</span><span class="sxs-lookup"><span data-stu-id="b6beb-152">**Remove the semantic language statistics database.**</span></span>  
 <span data-ttu-id="b6beb-153">데이터베이스를 등록 취소하고 분리한 후 데이터베이스 파일을 간단히 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-153">After unregistering and detaching the database, you can simply delete the database file.</span></span> <span data-ttu-id="b6beb-154">제거 프로그램은 없으며 제어판의 **프로그램 및 기능** 에도 해당 항목이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-154">There is no uninstall program and there is no entry in **Programs and Features** in the Control Panel.</span></span>  
  
###  <a name="requirements-and-restrictions-for-installing-and-removing-the-semantic-language-statistics-database"></a><a name="reqinstall"></a><span data-ttu-id="b6beb-155">의미 체계 언어 통계 데이터베이스 설치 및 제거에 대 한 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="b6beb-155">Requirements and Restrictions for Installing and Removing the Semantic Language Statistics Database</span></span>  
  
-   <span data-ttu-id="b6beb-156">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]인스턴스별로 하나의 의미 체계 언어 통계 데이터베이스만 연결하고 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-156">You can only attach and register one semantic language statistics database on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="b6beb-157">단일 컴퓨터의 각 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스마다 의미 체계 언어 통계 데이터베이스의 물리적 복사본이 하나씩 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-157">Each instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on a single computer requires a separate physical copy of the semantic language statistics database.</span></span> <span data-ttu-id="b6beb-158">인스턴스마다 하나의 복사본을 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-158">Attach one copy to each instance.</span></span>  
  
-   <span data-ttu-id="b6beb-159">등록된 올바른 의미 체계 언어 통계 데이터베이스를 분리하고 이름이 동일한 임의의 데이터베이스로 바꿀 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-159">You cannot detach a valid and registered semantic language statistics database and replace it with an arbitrary database that has the same name.</span></span> <span data-ttu-id="b6beb-160">이렇게 하면 활성 또는 이후 인덱스 채우기가 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-160">Doing so will cause active or future index populations to fail.</span></span>  
  
-   <span data-ttu-id="b6beb-161">의미 체계 언어 통계 데이터베이스는 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-161">The semantic language statistics database is read-only.</span></span> <span data-ttu-id="b6beb-162">이 데이터베이스를 사용자 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-162">You cannot customize this database.</span></span> <span data-ttu-id="b6beb-163">어떤 식으로든 데이터베이스의 내용을 변경하면 이후 의미 체계 인덱싱의 결과는 신뢰할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-163">If you alter the content of the database in any way, the results for future semantic indexing are indeterministic.</span></span> <span data-ttu-id="b6beb-164">이 데이터의 원래 상태로 복원하려면 변경된 데이터베이스를 삭제하고 데이터베이스의 변경되지 않은 새 복사본을 다운로드하여 연결하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-164">To restore the original state of this data, you can drop the altered database, and download and attach a new and unaltered copy of the database.</span></span>  
  
-   <span data-ttu-id="b6beb-165">의미 체계 언어 통계 데이터베이스를 분리하거나 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-165">It is possible to detach or drop the semantic language statistics database.</span></span> <span data-ttu-id="b6beb-166">데이터베이스에 대 한 읽기 잠금을 가진 활성 인덱싱 작업이 있는 경우에는 분리 또는 삭제 작업이 실패 하거나 시간 초과 됩니다. 이는 기존 동작과 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-166">If there are any active indexing operations that have read locks on the database, then the detach or drop operation will fail or time out. This is consistent with existing behavior.</span></span> <span data-ttu-id="b6beb-167">데이터베이스를 제거하면 의미 체계 인덱싱 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-167">After the database is removed, semantic indexing operations will fail.</span></span>  
  
## <a name="installing-optional-support-for-newer-document-types"></a><span data-ttu-id="b6beb-168">최신 문서 유형에 대한 선택적 지원 설치</span><span class="sxs-lookup"><span data-stu-id="b6beb-168">Installing Optional Support for Newer Document Types</span></span>  
  
###  <a name="how-to-install-the-latest-filters-for-microsoft-office-and-other-microsoft-document-types"></a><a name="office"></a><span data-ttu-id="b6beb-169">방법: Microsoft Office 및 기타 Microsoft 문서 유형에 대 한 최신 필터 설치</span><span class="sxs-lookup"><span data-stu-id="b6beb-169">How to: Install the Latest Filters for Microsoft Office and other Microsoft Document Types</span></span>  
 <span data-ttu-id="b6beb-170">이번 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 릴리스에서는 최신 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 단어 분리기 및 형태소 분석기를 설치하지만 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office 문서 및 다른 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 문서 유형용 최신 필터는 설치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-170">This release of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installs the latest [!INCLUDE[msCoName](../../../includes/msconame-md.md)] word breakers and stemmers, but does not install the latest filters for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office documents and other [!INCLUDE[msCoName](../../../includes/msconame-md.md)] document types.</span></span> <span data-ttu-id="b6beb-171">이 필터는 최신 버전의 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office 및 다른 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 애플리케이션을 사용하여 만든 문서를 인덱싱하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b6beb-171">These filters are required for indexing documents created with recent versions of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office and other [!INCLUDE[msCoName](../../../includes/msconame-md.md)] applications.</span></span> <span data-ttu-id="b6beb-172">최신 필터를 다운로드하려면 [Microsoft Office 2010 Filter Packs](https://www.microsoft.com/download/details.aspx?id=17062)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b6beb-172">To download the latest filters, see [Microsoft Office 2010 Filter Packs](https://www.microsoft.com/download/details.aspx?id=17062).</span></span>  
  
  

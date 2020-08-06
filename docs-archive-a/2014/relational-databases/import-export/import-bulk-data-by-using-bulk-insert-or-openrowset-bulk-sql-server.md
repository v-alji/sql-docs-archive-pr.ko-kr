---
title: BULK INSERT 또는 OPENROWSET(BULK...)를 사용하여 데이터 대량 가져오기(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- BULK INSERT statement, importing data from a remote data file
- bulk importing [SQL Server], methods
- bulk exporting [SQL Server], methods
- OPENROWSET function, BULK INSERT
- bulk importing [SQL Server], security
- bulk rowset providers [SQL Server]
- bulk exporting [SQL Server], BULK INSERT statement
- remote data access [SQL Server], bulk importing
- bulk importing [SQL Server], BULK INSERT statement
- Transact-SQL bulk export/import operations
ms.assetid: 18a64236-0285-46ea-8929-6ee9bcc020b9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: be36167020b96dba6d494685d958c38e0e6afbba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653374"
---
# <a name="import-bulk-data-by-using-bulk-insert-or-openrowsetbulk-sql-server"></a><span data-ttu-id="3ad3c-102">BULK INSERT 또는 OPENROWSET(BULK...)를 사용하여 데이터 대량 가져오기</span><span class="sxs-lookup"><span data-stu-id="3ad3c-102">Import Bulk Data by Using BULK INSERT or OPENROWSET(BULK...) (SQL Server)</span></span>
  <span data-ttu-id="3ad3c-103">이 항목에서는 [!INCLUDE[tsql](../../includes/tsql-md.md)] BULK INSERT 문 및 INSERT...SELECT \* FROM OPENROWSET(BULK...) 문을 사용하여 데이터 파일의 데이터를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에 대량으로 가져오는 방법을 간략하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-103">This topic provides an overview of how to use the [!INCLUDE[tsql](../../includes/tsql-md.md)] BULK INSERT statement and the INSERT...SELECT \* FROM OPENROWSET(BULK...) statement to bulk import data from a data file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="3ad3c-104">또한 BULK INSERT 및 OPENROWSET(BULK…)을 사용할 때와 이러한 방법을 사용하여 원격 데이터 원본에서 데이터를 대량으로 가져올 때의 보안 고려 사항에 대해서도 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-104">This topic also describes security considerations for using BULK INSERT and OPENROWSET(BULK...), and using these methods to bulk import from a remote data source.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ad3c-105">BULK INSERT 또는 OPENROWSET(BULK…)을 사용할 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전에서 가장을 처리하는 방법을 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-105">When you use BULK INSERT or OPENROWSET(BULK...), it is important to understand how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version handles impersonation.</span></span> <span data-ttu-id="3ad3c-106">자세한 내용은 이 항목의 뒷부분에 나오는 "보안 고려 사항"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-106">For more information, see "Security Considerations," later in this topic.</span></span>  
  
## <a name="bulk-insert-statement"></a><span data-ttu-id="3ad3c-107">BULK INSERT 문</span><span class="sxs-lookup"><span data-stu-id="3ad3c-107">BULK INSERT Statement</span></span>  
 <span data-ttu-id="3ad3c-108">BULK INSERT는 데이터 파일의 데이터를 테이블로 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-108">BULK INSERT loads data from a data file into a table.</span></span> <span data-ttu-id="3ad3c-109">이 기능은 **bcp** 명령의 **in** 옵션이 제공하는 기능과 유사하지만 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스에서 데이터 파일을 읽는다는 점이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-109">This functionality is similar to that provided by the **in** option of the **bcp** command; however, the data file is read by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span> <span data-ttu-id="3ad3c-110">BULK INSERT 구문에 대한 자세한 내용은 [BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-110">For a description of the BULK INSERT syntax, see [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
### <a name="examples"></a><span data-ttu-id="3ad3c-111">예</span><span class="sxs-lookup"><span data-stu-id="3ad3c-111">Examples</span></span>  
 <span data-ttu-id="3ad3c-112">BULK INSERT 예를 보려면 다음을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-112">For BULK INSERT examples, see:</span></span>  
  
-   [<span data-ttu-id="3ad3c-113">BULK INSERT&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3ad3c-113">BULK INSERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/bulk-insert-transact-sql)  
  
-   [<span data-ttu-id="3ad3c-114">XML 문서 대량 가져오기 및 내보내기 예제&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3ad3c-114">Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;</span></span>](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [<span data-ttu-id="3ad3c-115">데이터 대량 가져오기 중 ID 값 유지&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3ad3c-115">Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;</span></span>](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [<span data-ttu-id="3ad3c-116">대량 가져오기 수행 중 Null 유지 또는 기본값 사용&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3ad3c-116">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [<span data-ttu-id="3ad3c-117">필드 및 행 종결자 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3ad3c-117">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](specify-field-and-row-terminators-sql-server.md)  
  
-   [<span data-ttu-id="3ad3c-118">서식 파일을 사용하여 데이터 대량 가져오기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3ad3c-118">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="3ad3c-119">문자 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3ad3c-119">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="3ad3c-120">네이티브 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3ad3c-120">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="3ad3c-121">유니코드 문자 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3ad3c-121">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="3ad3c-122">유니코드 네이티브 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3ad3c-122">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="3ad3c-123">서식 파일을 사용하여 테이블 열 건너뛰기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3ad3c-123">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [<span data-ttu-id="3ad3c-124">서식 파일을 사용하여 테이블 열을 데이터 파일 필드에 매핑&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3ad3c-124">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="openrowsetbulk-function"></a><span data-ttu-id="3ad3c-125">OPENROWSET(BULK...) 함수</span><span class="sxs-lookup"><span data-stu-id="3ad3c-125">OPENROWSET(BULK...) Function</span></span>  
 <span data-ttu-id="3ad3c-126">OPENROWSET 대량 행 집합 공급자는 OPENROWSET 함수를 호출하고 BULK 옵션을 지정하여 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-126">The OPENROWSET bulk rowset provider is accessed by calling the OPENROWSET function and specifying the BULK option.</span></span> <span data-ttu-id="3ad3c-127">OPENROWSET(BULK...) 함수를 사용하면 OLE DB 공급 기업을 통해 데이터 파일 등의 원격 데이터 원본에 연결하여 원격 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-127">The OPENROWSET(BULK...) function allows you to access remote data by connecting to a remote data source, such as a data file, through an OLE DB provider.</span></span>  
  
 <span data-ttu-id="3ad3c-128">데이터를 대량으로 가져오려면 INSERT 문 내의 SELECT...FROM 절에서 OPENROWSET(BULK...)를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-128">To bulk import data, call OPENROWSET(BULK...) from a SELECT...FROM clause within an INSERT statement.</span></span> <span data-ttu-id="3ad3c-129">데이터 대량 가져오기의 기본 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-129">The basic syntax for bulk importing data is:</span></span>  
  
 <span data-ttu-id="3ad3c-130">INSERT ... 선택 \* OPENROWSET (BULK)에서</span><span class="sxs-lookup"><span data-stu-id="3ad3c-130">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>  
  
 <span data-ttu-id="3ad3c-131">INSERT 문에서 사용하는 경우 OPENROWSET(BULK...)은 테이블 힌트를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-131">When used in an INSERT statement, OPENROWSET(BULK...) supports table hints.</span></span> <span data-ttu-id="3ad3c-132">또한 TABLOCK과 같은 일반적인 테이블 힌트 외에도 BULK 절에는 다음과 같은 특수 테이블 힌트를 사용할 수 있습니다. IGNORE_CONSTRAINTS(CHECK 제약 조건만 무시), IGNORE_TRIGGERS, KEEPDEFAULTS 및 KEEPIDENTITY.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-132">In addition to the regular table hints, such as TABLOCK, the BULK clause can accept the following specialized table hints: IGNORE_CONSTRAINTS (ignores only the CHECK constraints), IGNORE_TRIGGERS, KEEPDEFAULTS, and KEEPIDENTITY.</span></span> <span data-ttu-id="3ad3c-133">자세한 내용은 [테이블 힌트&#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-133">For more information, see [Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table).</span></span>  
  
 <span data-ttu-id="3ad3c-134">BULK 옵션의 추가 사용법에 대한 자세한 내용은 [OPENROWSET&#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-134">For information about additional uses of the BULK option, see [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
### <a name="examples"></a><span data-ttu-id="3ad3c-135">예</span><span class="sxs-lookup"><span data-stu-id="3ad3c-135">Examples</span></span>  
 <span data-ttu-id="3ad3c-136">INSERT...SELECT \* FROM OPENROWSET(BULK...) 문의 예는 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-136">For examples of INSERT...SELECT \* FROM OPENROWSET(BULK...) statements, see the following topics:</span></span>  
  
-   [<span data-ttu-id="3ad3c-137">XML 문서 대량 가져오기 및 내보내기 예제&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3ad3c-137">Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;</span></span>](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [<span data-ttu-id="3ad3c-138">데이터 대량 가져오기 중 ID 값 유지&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3ad3c-138">Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;</span></span>](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [<span data-ttu-id="3ad3c-139">대량 가져오기 수행 중 Null 유지 또는 기본값 사용&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3ad3c-139">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [<span data-ttu-id="3ad3c-140">서식 파일을 사용하여 데이터 대량 가져오기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3ad3c-140">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="3ad3c-141">문자 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3ad3c-141">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="3ad3c-142">서식 파일을 사용하여 테이블 열 건너뛰기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3ad3c-142">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [<span data-ttu-id="3ad3c-143">서식 파일을 사용하여 데이터 필드 건너뛰기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3ad3c-143">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="3ad3c-144">서식 파일을 사용하여 테이블 열을 데이터 파일 필드에 매핑&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3ad3c-144">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="security-considerations"></a><span data-ttu-id="3ad3c-145">보안 고려사항</span><span class="sxs-lookup"><span data-stu-id="3ad3c-145">Security Considerations</span></span>  
 <span data-ttu-id="3ad3c-146">사용자가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 사용하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스 계정의 보안 프로필이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-146">If a user uses a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login, the security profile of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process account is used.</span></span> <span data-ttu-id="3ad3c-147">SQL Server 인증을 사용하는 로그인은 데이터베이스 엔진 외부에서 인증될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-147">A login using SQL Server authentication cannot be authenticated outside of the Database Engine.</span></span> <span data-ttu-id="3ad3c-148">따라서 BULK INSERT 명령이 SQL Server 인증을 사용하는 로그인에 의해 시작되면 데이터에 대한 연결이 SQL Server 프로세스 계정(SQL Server 데이터베이스 엔진 서비스에서 사용하는 계정)의 보안 컨텍스트를 사용하여 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-148">Therefore, when a BULK INSERT command is initiated by a login using SQL Server authentication, the connection to the data is made using the security context of the SQL Server process account (the account used by the SQL Server Database Engine service).</span></span> <span data-ttu-id="3ad3c-149">원본 데이터를 성공적으로 읽으려면 SQL Server 데이터베이스 엔진에서 사용하는 계정에 원본 데이터에 대한 액세스 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-149">To successfully read the source data you must grant the account used by the SQL Server Database Engine, access to the source data.</span></span> <span data-ttu-id="3ad3c-150">반면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용자가 Windows 인증을 사용하여 로그온한 경우에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스의 보안 프로필에 관계없이 해당 사용자 계정으로 액세스할 수 있는 파일만 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-150">In contrast, if a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user logs on by using Windows Authentication, the user can read only those files that can be accessed by the user account, regardless of the security profile of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span>  
  
 <span data-ttu-id="3ad3c-151">예를 들어 Windows 인증을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 로그온한 사용자가 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-151">For example, consider a user who logged in to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using Windows Authentication.</span></span> <span data-ttu-id="3ad3c-152">이 사용자가 BULK INSERT 또는 OPENROWSET을 사용하여 데이터 파일의 데이터를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블로 가져오려면 사용자 계정에 해당 데이터 파일에 대한 읽기 액세스 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-152">For the user to be able to use BULK INSERT or OPENROWSET to import data from a data file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table, the user account requires read access to the data file.</span></span> <span data-ttu-id="3ad3c-153">해당 데이터 파일에 대한 액세스 권한이 있는 사용자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스에 해당 파일에 대한 액세스 권한이 없더라도 해당 파일의 데이터를 테이블로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-153">With access to the data file, the user can import data from the file into a table even if the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process does not have permission to access the file.</span></span> <span data-ttu-id="3ad3c-154">이때 사용자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스에 파일 액세스 권한을 부여할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-154">The user does not have to grant file-access permission to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3ad3c-155">및 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 인증된 Windows 사용자의 자격 증명을 전달하여 다른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결할 수 있도록 구성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-155">and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows can be configured to enable an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to connect to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by forwarding the credentials of an authenticated Windows user.</span></span> <span data-ttu-id="3ad3c-156">이러한 작업을 *가장* 또는 *위임*이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-156">This arrangement is known as *impersonation* or *delegation*.</span></span> <span data-ttu-id="3ad3c-157">BULK INSERT 또는 OPENROWSET을 사용할 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전에서 사용자 가장에 대한 보안을 처리하는 방법을 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-157">Understanding how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version handle security for user impersonation is important when you use BULK INSERT or OPENROWSET.</span></span> <span data-ttu-id="3ad3c-158">사용자 가장을 사용하면 데이터 파일을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스 또는 사용자와는 다른 컴퓨터에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-158">User impersonation allows the data file to reside on a different computer than either the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process or the user.</span></span> <span data-ttu-id="3ad3c-159">예를 들어 **Computer_A** 의 사용자에게 **Computer_B**의 데이터 파일에 대한 액세스 권한이 있고 자격 증명의 위임이 적절하게 설정되어 있는 경우 해당 사용자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Computer_C **에서 실행 중인**인스턴스에 연결하고 **Computer_B**의 데이터 파일에 액세스하여 해당 파일의 데이터를 **Computer_C**의 테이블로 대량 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-159">For example, if a user on **Computer_A** has access to a data file on **Computer_B**, and the delegation of credentials has been set appropriately, the user can connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is running on **Computer_C**, access the data file on **Computer_B**, and bulk import data from that file into a table on **Computer_C**.</span></span>  
  
## <a name="bulk-importing-from-a-remote-data-file"></a><span data-ttu-id="3ad3c-160">원격 데이터 파일에서 대량 가져오기</span><span class="sxs-lookup"><span data-stu-id="3ad3c-160">Bulk Importing from a Remote Data File</span></span>  
 <span data-ttu-id="3ad3c-161">BULK INSERT 또는 INSERT...SELECT \* FROM OPENROWSET(BULK...)를 사용하여 다른 컴퓨터에서 데이터를 대량으로 가져오려면 두 컴퓨터 간에 데이터 파일을 공유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-161">To use BULK INSERT or INSERT...SELECT \* FROM OPENROWSET(BULK...) to bulk import data from another computer, the data file must be shared between the two computers.</span></span> <span data-ttu-id="3ad3c-162">공유 데이터 파일을 지정하려면 **\\\\** _Servername_ **\\** _Sharename_ **\\** _Path_ **\\** _Filename_의 일반 형식으로 해당 UNC(범용 명명 규칙) 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-162">To specify a shared data file, use its universal naming convention (UNC) name, which takes the general form, **\\\\**_Servername_**\\**_Sharename_**\\**_Path_**\\**_Filename_.</span></span> <span data-ttu-id="3ad3c-163">또한 데이터 파일을 액세스하는 데 사용되는 계정에는 원격 디스크의 파일을 읽는 데 필요한 사용 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-163">Additionally, the account used to access the data file must have the permissions that are required for reading the file on the remote disk.</span></span>  
  
 <span data-ttu-id="3ad3c-164">예를 들어 다음 `BULK INSERT` 문은 `SalesOrderDetail` 라는 데이터 파일의 데이터를 `AdventureWorks` 데이터베이스의 `newdata.txt`테이블로 대량 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-164">For example, the following `BULK INSERT` statement bulk imports data into the `SalesOrderDetail` table of the `AdventureWorks` database from a data file that is named `newdata.txt`.</span></span> <span data-ttu-id="3ad3c-165">이 데이터 파일은 `\dailyorders` 시스템의 네트워크 공유 디렉터리 `salesforce` 에서 공유 폴더 `computer2`에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-165">This data file resides in a shared folder named `\dailyorders` on a network share directory named `salesforce` on a system named `computer2`.</span></span>  
  
```  
BULK INSERT AdventureWorks2012.Sales.SalesOrderDetail  
   FROM '\\computer2\salesforce\dailyorders\neworders.txt';  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="3ad3c-166">클라이언트는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 독립적으로 파일을 읽기 때문에 **bcp** 유틸리티에는 이러한 제한 사항이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3ad3c-166">This restriction does not apply to the **bcp** utility because the client reads the file independently of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ad3c-167">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3ad3c-167">See Also</span></span>  
 <span data-ttu-id="3ad3c-168">[INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3ad3c-168">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span></span>  
 <span data-ttu-id="3ad3c-169">[SELECT 절&#40;Transact-SQL&#41;](/sql/t-sql/queries/select-clause-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3ad3c-169">[SELECT Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-clause-transact-sql) </span></span>  
 <span data-ttu-id="3ad3c-170">[데이터 대량 가져오기 및 내보내기&#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3ad3c-170">[Bulk Import and Export of Data &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span></span>  
 <span data-ttu-id="3ad3c-171">[OPENROWSET&#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3ad3c-171">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="3ad3c-172">[SELECT&#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3ad3c-172">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 <span data-ttu-id="3ad3c-173">[FROM&#40;Transact-SQL&#41;](/sql/t-sql/queries/from-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3ad3c-173">[FROM &#40;Transact-SQL&#41;](/sql/t-sql/queries/from-transact-sql) </span></span>  
 <span data-ttu-id="3ad3c-174">[bcp 유틸리티](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="3ad3c-174">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 [<span data-ttu-id="3ad3c-175">BULK INSERT&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3ad3c-175">BULK INSERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/bulk-insert-transact-sql)  
  
  

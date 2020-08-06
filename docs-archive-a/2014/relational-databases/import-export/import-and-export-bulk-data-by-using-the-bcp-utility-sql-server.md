---
title: bcp 유틸리티를 사용하여 대량 데이터 가져오기 및 내보내기(SQL Server) | Microsoft 문서
ms.prod: sql-server-2014
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk exporting [SQL Server], bcp utility
- bulk importing [SQL Server], bcp utility
- bcp utility [SQL Server], about bcp utility
ms.assetid: 73e949de-67a3-4c84-9735-7da1ad4ba34a
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: ''
ms.date: 06/14/2017
ms.openlocfilehash: 7d1892b26f3c638a696d8ed15e739f56ac2e682f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653375"
---
# <a name="import-and-export-bulk-data-by-using-the-bcp-utility-sql-server"></a><span data-ttu-id="a7132-102">bcp 유틸리티를 사용하여 대량 데이터 가져오기 및 내보내기(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a7132-102">Import and Export Bulk Data by Using the bcp Utility (SQL Server)</span></span>

<span data-ttu-id="a7132-103">이 항목에서는 분할된 뷰를 포함하여 SELECT 문이 작동하는 [데이터베이스의 어디에서나 데이터를 가져올 수 있도록](../../tools/bcp-utility.md) bcp 유틸리티 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 사용하는 방법에 대해 간략하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a7132-103">This topic provides an overview for using the [bcp utility](../../tools/bcp-utility.md) to export data from anywhere in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database where a SELECT statement works, including partitioned views.</span></span>  
  
 <span data-ttu-id="a7132-104">bcp 유틸리티(Bcp.exe)는 BCP(대량 복사 프로그램) API를 사용하는 명령줄 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="a7132-104">The bcp utility (Bcp.exe) is a command-line tool that uses the Bulk Copy Program (BCP) API.</span></span> <span data-ttu-id="a7132-105">bcp 유틸리티는 다음 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a7132-105">The bcp utility performs the following tasks:</span></span>  
  
-   <span data-ttu-id="a7132-106">데이터 파일로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블의 데이터를 대량으로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="a7132-106">Bulk exports data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table into a data file.</span></span>  
  
-   <span data-ttu-id="a7132-107">쿼리의 데이터를 대량으로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="a7132-107">Bulk exports data from a query.</span></span>  
  
-   <span data-ttu-id="a7132-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블로 데이터 파일의 데이터를 대량으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a7132-108">Bulk imports data from a data file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
-   <span data-ttu-id="a7132-109">서식 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="a7132-109">Generates format files.</span></span>  
  
 <span data-ttu-id="a7132-110">**bcp** 명령을 통해 bcp 유틸리티에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="a7132-110">The bcp utility is accessed by the **bcp** command.</span></span> <span data-ttu-id="a7132-111">기존 서식 파일을 사용하지 않는 경우 **bcp** 명령을 사용하여 데이터를 대량으로 가져오려면 테이블의 스키마와 열의 데이터 형식을 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7132-111">To use the **bcp** command to bulk import data, you must understand the schema of the table and the data types of its columns, unless you are using a pre-existing format file.</span></span>  
  
 <span data-ttu-id="a7132-112">bcp 유틸리티는 다른 프로그램에서 사용할 수 있도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블의 데이터를 데이터 파일로 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7132-112">The bcp utility can export data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table to a data file for use in other programs.</span></span> <span data-ttu-id="a7132-113">또한 이 유틸리티는 일반적으로 DBMS(데이터베이스 관리 시스템)와 같은 다른 프로그램의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블로 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7132-113">The utility can also import data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table from another program, usually another database management system (DBMS).</span></span> <span data-ttu-id="a7132-114">원본 프로그램에서 데이터 파일로 데이터를 내보낸 다음 별도의 작업으로 데이터 파일에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블로 데이터를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="a7132-114">The data is first exported from the source program to a data file and then, in a separate operation, copied from the data file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="a7132-115">**bcp** 명령은 데이터 파일의 데이터 형식과 기타 정보를 지정하는 데 사용하는 스위치를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a7132-115">The **bcp** command provides switches that you use to specify the data type of the data file and other information.</span></span> <span data-ttu-id="a7132-116">이러한 스위치가 지정되지 않은 경우 해당 명령은 데이터 파일의 데이터 필드 유형과 같은 서식 정보를 확인하는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a7132-116">If these switches are not specified, the command prompts for formatting information, such as the type of data fields in a data file.</span></span> <span data-ttu-id="a7132-117">그런 다음 명령은 대화형 응답을 포함하여 서식 파일을 만들 것인지 묻습니다.</span><span class="sxs-lookup"><span data-stu-id="a7132-117">The command then asks whether you want to create a format file that contains your interactive responses.</span></span> <span data-ttu-id="a7132-118">나중에 융통성 있게 대량으로 가져오기 또는 내보내기 작업을 수행하려면 서식 파일이 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="a7132-118">If you want flexibility for future bulk-import or bulk-export operations, a format file is often useful.</span></span> <span data-ttu-id="a7132-119">나중에 해당 데이터 파일에 대해 **bcp** 명령을 실행할 때 서식 파일을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7132-119">You can specify the format file on later **bcp** commands for equivalent data files.</span></span> <span data-ttu-id="a7132-120">자세한 내용은 [bcp를 사용하여 데이터 형식을 호환 가능하도록 지정&#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a7132-120">For more information, see [Specify Data Formats for Compatibility when Using bcp &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a7132-121">bcp 유틸리티가 ODBC 대량 복사를 사용하여 작성됨</span><span class="sxs-lookup"><span data-stu-id="a7132-121">The bcp utility is written by using the ODBC bulk-copy</span></span>  
  
 <span data-ttu-id="a7132-122">**bcp** 명령 구문에 대한 자세한 내용은 [bcp Utility](../../tools/bcp-utility.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a7132-122">For a description of the **bcp** command syntax, see [bcp Utility](../../tools/bcp-utility.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a7132-123">예</span><span class="sxs-lookup"><span data-stu-id="a7132-123">Examples</span></span>

 <span data-ttu-id="a7132-124">**bcp** 예제는 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a7132-124">For **bcp** examples, see:</span></span>  
  
-   [<span data-ttu-id="a7132-125">bcp 유틸리티</span><span class="sxs-lookup"><span data-stu-id="a7132-125">bcp Utility</span></span>](../../tools/bcp-utility.md)  
  
-   [<span data-ttu-id="a7132-126">서식 파일 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a7132-126">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="a7132-127">XML 문서 대량 가져오기 및 내보내기 예제&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a7132-127">Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;</span></span>](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [<span data-ttu-id="a7132-128">데이터 대량 가져오기 중 ID 값 유지&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a7132-128">Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;</span></span>](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [<span data-ttu-id="a7132-129">대량 가져오기 수행 중 Null 유지 또는 기본값 사용&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a7132-129">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [<span data-ttu-id="a7132-130">필드 및 행 종결자 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a7132-130">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](specify-field-and-row-terminators-sql-server.md)  
  
-   [<span data-ttu-id="a7132-131">서식 파일을 사용하여 데이터 대량 가져오기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a7132-131">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="a7132-132">문자 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a7132-132">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="a7132-133">네이티브 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a7132-133">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="a7132-134">유니코드 문자 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a7132-134">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="a7132-135">유니코드 네이티브 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a7132-135">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  

## <a name="see-also"></a><span data-ttu-id="a7132-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a7132-136">See Also</span></span>

<span data-ttu-id="a7132-137">[&#40;transact-sql&#41;삽입](/sql/t-sql/statements/insert-transact-sql) 
 [SELECT 절 &#40;transact-sql&#41;](/sql/t-sql/queries/select-clause-transact-sql) 
 [Bcp 유틸리티](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="a7132-137">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)
[SELECT Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-clause-transact-sql)
[bcp Utility](../../tools/bcp-utility.md) </span></span>  
<span data-ttu-id="a7132-138">[SQL Server&#41;](prepare-to-bulk-import-data-sql-server.md) 
 &#40;대량으로 데이터 가져오기 준비 [Transact-sql&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) 
 BULK INSERT &#40;[데이터 &#40;SQL Server 대량 가져오기 및 내보내기&#41;](bulk-import-and-export-of-data-sql-server.md) 
 [OPENROWSET &#40;transact-sql&#41;](/sql/t-sql/functions/openrowset-transact-sql) 
 [SQL Server&#41;&#40;서식 파일 만들기](create-a-format-file-sql-server.md)</span><span class="sxs-lookup"><span data-stu-id="a7132-138">[Prepare to Bulk Import Data &#40;SQL Server&#41;](prepare-to-bulk-import-data-sql-server.md)
[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)
[Bulk Import and Export of Data &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md)
[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)
[Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md)</span></span>
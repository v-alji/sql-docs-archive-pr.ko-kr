---
title: bcp 유틸리티 | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- bcp utility [SQL Server]
- exporting data
- row exporting [SQL Server]
- copying data [SQL Server], bcp utility
- command prompt utilities [SQL Server], bcp
- tables [SQL Server], importing data
- column importing [SQL Server]
- bcp utility [SQL Server], command options
- file exporting [SQL Server]
- bulk copy [SQL Server]
- bcp utility [SQL Server], about bcp utility
- tables [SQL Server], exporting data
- row importing [SQL Server]
- importing data, bcp utility
- file importing [SQL Server]
- column exporting [SQL Server]
ms.assetid: c0af54f5-ca4a-4995-a3a4-0ce39c30ec38
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0ddc4c4e7023a83bfde9295a1410e7db5cb90b84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651412"
---
# <a name="bcp-utility"></a><span data-ttu-id="31507-102">bcp 유틸리티</span><span class="sxs-lookup"><span data-stu-id="31507-102">bcp Utility</span></span>
  <span data-ttu-id="31507-103">**Bcp** 유틸리티는 인스턴스와 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 사용자가 지정한 형식의 데이터 파일 간에 데이터를 대량 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-103">The **bcp** utility bulk copies data between an instance of [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and a data file in a user-specified format.</span></span> <span data-ttu-id="31507-104">**bcp** 유틸리티를 사용하여 많은 수의 새 행을 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 테이블로 가져오거나 테이블에서 데이터 파일로 데이터를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-104">The **bcp** utility can be used to import large numbers of new rows into [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tables or to export data out of tables into data files.</span></span> <span data-ttu-id="31507-105">**queryout** 옵션과 함께 사용하는 경우를 제외하고 이 유틸리티를 사용하는 데에는 [!INCLUDE[tsql](../includes/tsql-md.md)]에 대한 지식이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-105">Except when used with the **queryout** option, the utility requires no knowledge of [!INCLUDE[tsql](../includes/tsql-md.md)].</span></span> <span data-ttu-id="31507-106">테이블로 데이터를 가져오려면 해당 테이블에 대해 만든 서식 파일을 사용하거나 이 테이블의 열에 적합한 테이블 구조와 데이터 형식을 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-106">To import data into a table, you must either use a format file created for that table or understand the structure of the table and the types of data that are valid for its columns.</span></span>  
  
 <span data-ttu-id="31507-107">![항목 링크 아이콘](../../2014/database-engine/media/topic-link.gif "항목 링크 아이콘")**bcp** 구문에 사용되는 구문 표기 규칙에 대한 자세한 내용은 [Transact-SQL 구문 표기 규칙&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31507-107">![Topic link icon](../../2014/database-engine/media/topic-link.gif "Topic link icon") For the syntax conventions that are used for the **bcp** syntax, see [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="31507-108">**bcp** 를 사용하여 데이터를 백업하는 경우 서식 파일을 만들어 데이터 서식을 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-108">If you use **bcp** to back up your data, create a format file to record the data format.</span></span> <span data-ttu-id="31507-109">**bcp** 데이터 파일에는 스키마 또는 서식 정보가 포함되어 있지 않기 때문에 테이블이나 뷰가 삭제된 경우 서식 파일이 없으면 데이터를 가져오지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-109">**bcp** data files do not include any schema or format information, so if a table or view is dropped and you do not have a format file, you may be unable to import the data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31507-110">구문</span><span class="sxs-lookup"><span data-stu-id="31507-110">Syntax</span></span>  
  
```  
  
   bcp [database_name.] schema.{table_name | view_name | "query" {indata_file | outdata_file | queryoutdata_file | format nul}  
  
[-apacket_size]  
[-bbatch_size]  
[-c]  
[-C { ACP | OEM | RAW | code_page } ]  
[-ddatabase_name]  
[-eerr_file]  
[-E]  
[-fformat_file]  
[-Ffirst_row]  
[-h"hint [,...n]"]   
[-iinput_file]  
[-k]  
[-Kapplication_intent]  
[-Llast_row]  
[-mmax_errors]  
[-n]  
[-N]  
[-ooutput_file]  
[-Ppassword]  
[-q]  
[-rrow_term]  
[-R]  
[-S [server_name[\instance_name]]  
[-tfield_term]  
[-T]  
[-Ulogin_id]  
[-v]  
[-V (80 | 90 | 100 | 110)]  
[-w]  
[-x]  
/?  
```  
  
## <a name="arguments"></a><span data-ttu-id="31507-111">인수</span><span class="sxs-lookup"><span data-stu-id="31507-111">Arguments</span></span>  
 <span data-ttu-id="31507-112">*data_file*</span><span class="sxs-lookup"><span data-stu-id="31507-112">*data_file*</span></span>  
 <span data-ttu-id="31507-113">데이터 파일의 전체 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="31507-113">Is the full path of the data file.</span></span> <span data-ttu-id="31507-114">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]로 데이터를 대량으로 가져오는 경우 데이터 파일에는 지정한 테이블 또는 뷰로 복사할 데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-114">When data is bulk imported into [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the data file contains the data to be copied into the specified table or view.</span></span> <span data-ttu-id="31507-115">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서 데이터를 대량으로 내보내는 경우 데이터 파일에는 테이블 또는 뷰에서 복사한 데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-115">When data is bulk exported from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the data file contains the data copied from the table or view.</span></span> <span data-ttu-id="31507-116">데이터 파일 경로는 1에서 255자까지 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-116">The path can have from 1 through 255 characters.</span></span> <span data-ttu-id="31507-117">데이터 파일에는 최대 2 개의<sup>63</sup> -1 개의 행이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-117">The data file can contain a maximum of 2<sup>63</sup> - 1 rows.</span></span>  
  
 <span data-ttu-id="31507-118">*database_name*</span><span class="sxs-lookup"><span data-stu-id="31507-118">*database_name*</span></span>  
 <span data-ttu-id="31507-119">지정한 테이블 또는 뷰가 있는 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="31507-119">Is the name of the database in which the specified table or view resides.</span></span> <span data-ttu-id="31507-120">이 인수를 지정하지 않으면 사용자의 기본 데이터베이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-120">If not specified, this is the default database for the user.</span></span>  
  
 <span data-ttu-id="31507-121">`d-`를 사용하여 데이터베이스 이름을 명시적으로 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-121">You can also explicitly specify the database name with `d-`.</span></span>  
  
 <span data-ttu-id="31507-122">**in** _data_file_  |  **out**_data_file_  |  **queryout**_data_file_  |  **형식 nul**</span><span class="sxs-lookup"><span data-stu-id="31507-122">**in** _data_file_ | **out**_data_file_ | **queryout**_data_file_ | **format nul**</span></span>  
 <span data-ttu-id="31507-123">다음과 같이 대량 복사 방향을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-123">Specifies the direction of the bulk copy, as follows:</span></span>  
  
-   <span data-ttu-id="31507-124">**in** 은 파일에서 데이터베이스 테이블 또는 뷰로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-124">**in** copies from a file into the database table or view.</span></span>  
  
-   <span data-ttu-id="31507-125">**out** 은 데이터베이스 테이블 또는 뷰에서 파일로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-125">**out** copies from the database table or view to a file.</span></span> <span data-ttu-id="31507-126">기존 파일을 지정하면 이 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="31507-126">If you specify an existing file, the file is overwritten.</span></span> <span data-ttu-id="31507-127">데이터를 추출할 때 **bcp** 유틸리티는 빈 문자열을 null로 나타내고 null 문자열은 빈 문자열로 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="31507-127">When extracting data, note that the **bcp** utility represents an empty string as a null and a null string as an empty string.</span></span>  
  
-   <span data-ttu-id="31507-128">**queryout** 은 쿼리에서 복사하며 쿼리에서 데이터를 대량 복사하는 경우에만 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-128">**queryout** copies from a query and must be specified only when bulk copying data from a query.</span></span>  
  
-   <span data-ttu-id="31507-129">**format** 은 지정 된 옵션 (**-n**, `-c` , `-w` 또는 **-n**)과 테이블 또는 뷰 구분 기호를 기반으로 서식 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="31507-129">**format** creates a format file based on the option specified (**-n**, `-c`, `-w`, or **-N**) and the table or view delimiters.</span></span> <span data-ttu-id="31507-130">데이터를 대량 복사 하는 경우 **bcp** 명령은 서식 파일을 참조할 수 있으므로 대화형으로 서식 정보를 다시 입력할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-130">When bulk copying data, the **bcp** command can refer to a format file, which saves you from re-entering format information interactively.</span></span> <span data-ttu-id="31507-131">**format** 옵션에는 **-f** 옵션이 필요하며 XML 서식 파일을 만드는 경우 **-x** 옵션도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-131">The **format** option requires the **-f** option; creating an XML format file, also requires the **-x** option.</span></span> <span data-ttu-id="31507-132">자세한 내용은 [서식 파일 만들기&#40;SQL Server&#41;](../relational-databases/import-export/create-a-format-file-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31507-132">For more information, see [Create a Format File &#40;SQL Server&#41;](../relational-databases/import-export/create-a-format-file-sql-server.md).</span></span> <span data-ttu-id="31507-133">**nul** 을 값으로 지정해야 합니다(**format nul**).</span><span class="sxs-lookup"><span data-stu-id="31507-133">You must specify **nul** as the value (**format nul**).</span></span>  
  
 <span data-ttu-id="31507-134">*owner*</span><span class="sxs-lookup"><span data-stu-id="31507-134">*owner*</span></span>  
 <span data-ttu-id="31507-135">테이블 또는 뷰의 소유자 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="31507-135">Is the name of the owner of the table or view.</span></span> <span data-ttu-id="31507-136">작업을 수행하는 사용자가 지정한 테이블 또는 뷰를 소유하고 있는 경우에는*owner* 를 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-136">*owner* is optional if the user performing the operation owns the specified table or view.</span></span> <span data-ttu-id="31507-137">*owner* 를 지정하지 않은 경우 작업을 수행하는 사용자가 지정한 테이블이나 뷰의 소유자가 아니면 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서 오류 메시지를 반환하고 작업이 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-137">If *owner* is not specified and the user performing the operation does not own the specified table or view, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] returns an error message, and the operation is canceled.</span></span>  
  
 <span data-ttu-id="31507-138">**"** _쿼리_ **"**</span><span class="sxs-lookup"><span data-stu-id="31507-138">**"** _query_ **"**</span></span>  
 <span data-ttu-id="31507-139">결과 집합을 반환하는 [!INCLUDE[tsql](../includes/tsql-md.md)] 쿼리입니다.</span><span class="sxs-lookup"><span data-stu-id="31507-139">Is a [!INCLUDE[tsql](../includes/tsql-md.md)] query that returns a result set.</span></span> <span data-ttu-id="31507-140">쿼리에서 여러 결과 집합을 반환하는 경우 첫 번째 결과 집합만 데이터 파일에 복사되고 그 다음 결과 집합은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-140">If the query returns multiple result sets, only the first result set is copied to the data file; subsequent result sets are ignored.</span></span> <span data-ttu-id="31507-141">쿼리는 큰따옴표로 묶고 쿼리 안에 포함되는 모든 것은 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-141">Use double quotation marks around the query and single quotation marks around anything embedded in the query.</span></span> <span data-ttu-id="31507-142">쿼리에서 데이터를 대량 복사할 때는**queryout** 도 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-142">**queryout** must also be specified when bulk copying data from a query.</span></span>  
  
 <span data-ttu-id="31507-143">쿼리는 bcp 문을 실행하기 전에 저장 프로시저 내에서 참조되는 모든 테이블이 존재하는 한 저장 프로시저를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-143">The query can reference a stored procedure as long as all tables referenced inside the stored procedure exist prior to executing the bcp statement.</span></span> <span data-ttu-id="31507-144">예를 들어 저장 프로시저가 임시 테이블을 생성하면 이 임시 테이블을 런타임에만 사용할 수 있고 문 실행 시에는 사용할 수 없기 때문에 **bcp** 문이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-144">For example, if the stored procedure generates a temp table, the **bcp** statement fails because the temp table is available only at run time and not at statement execution time.</span></span> <span data-ttu-id="31507-145">이 경우 테이블에 저장 프로시저 결과를 삽입한 다음 **bcp** 를 사용하여 테이블에서 데이터 파일로 데이터를 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-145">In this case, consider inserting the results of the stored procedure into a table and then use **bcp** to copy the data from the table into a data file.</span></span>  
  
 <span data-ttu-id="31507-146">*table_name*</span><span class="sxs-lookup"><span data-stu-id="31507-146">*table_name*</span></span>  
 <span data-ttu-id="31507-147">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 로 데이터를 가져올 때(**in**)는 대상 테이블의 이름이고 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서 데이터를 내보낼 때(**out**)는 원본 테이블의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="31507-147">Is the name of the destination table when importing data into [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (**in**), and the source table when exporting data from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (**out**).</span></span>  
  
 <span data-ttu-id="31507-148">*view_name*</span><span class="sxs-lookup"><span data-stu-id="31507-148">*view_name*</span></span>  
 <span data-ttu-id="31507-149">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 로 데이터를 복사할 때(**in**)는 대상 뷰의 이름이고 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서 데이터를 복사할 때(**out**)는 원본 뷰의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="31507-149">Is the name of the destination view when copying data into [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (**in**), and the source view when copying data from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (**out**).</span></span> <span data-ttu-id="31507-150">모든 열이 같은 테이블을 참조하는 뷰만 대상 뷰로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-150">Only views in which all columns refer to the same table can be used as destination views.</span></span> <span data-ttu-id="31507-151">뷰에 데이터를 복사하는 경우의 제한 사항에 대한 자세한 내용은 [INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31507-151">For more information on the restrictions for copying data into views, see [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql).</span></span>  
  
 <span data-ttu-id="31507-152">**-a** _packet_size_</span><span class="sxs-lookup"><span data-stu-id="31507-152">**-a** _packet_size_</span></span>  
 <span data-ttu-id="31507-153">서버에서 전송되거나 서버로 전송되는 네트워크 패킷당 바이트 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-153">Specifies the number of bytes, per network packet, sent to and from the server.</span></span> <span data-ttu-id="31507-154">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 또는 **sp_configure** 시스템 저장 프로시저를 사용하여 서버 구성 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-154">A server configuration option can be set by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] (or the **sp_configure** system stored procedure).</span></span> <span data-ttu-id="31507-155">그러나 이 옵션을 사용하여 서버 구성 옵션을 개별적으로 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-155">However, the server configuration option can be overridden on an individual basis by using this option.</span></span> <span data-ttu-id="31507-156">*packet_size* 는 4096 ~ 65535바이트일 수 있고 기본값은 4096입니다.</span><span class="sxs-lookup"><span data-stu-id="31507-156">*packet_size* can be from 4096 to 65535 bytes; the default is 4096.</span></span>  
  
 <span data-ttu-id="31507-157">패킷 크기가 커지면 대량 복사 작업의 성능이 향상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-157">Increased packet size can enhance performance of bulk-copy operations.</span></span> <span data-ttu-id="31507-158">더 큰 패킷을 요청했는데 허용되지 않으면 기본값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-158">If a larger packet is requested but cannot be granted, the default is used.</span></span> <span data-ttu-id="31507-159">**bcp** 유틸리티가 생성하는 성능 통계에는 사용되는 패킷의 크기가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="31507-159">The performance statistics generated by the **bcp** utility show the packet size used.</span></span>  
  
 <span data-ttu-id="31507-160">**-b** _batch_size_</span><span class="sxs-lookup"><span data-stu-id="31507-160">**-b** _batch_size_</span></span>  
 <span data-ttu-id="31507-161">가져온 데이터의 일괄 처리당 행 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-161">Specifies the number of rows per batch of imported data.</span></span> <span data-ttu-id="31507-162">각 일괄 처리는 커밋되기 전에 전체 일괄 처리를 가져오는 별도의 트랜잭션으로 가져오고 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-162">Each batch is imported and logged as a separate transaction that imports the whole batch before being committed.</span></span> <span data-ttu-id="31507-163">기본적으로 데이터 파일의 모든 행은 하나의 일괄 처리로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="31507-163">By default, all the rows in the data file are imported as one batch.</span></span> <span data-ttu-id="31507-164">여러 일괄 처리에 행을 분산시키려면 데이터 파일의 행 수보다 작은 *batch_size* 를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-164">To distribute the rows among multiple batches, specify a *batch_size* that is smaller than the number of rows in the data file.</span></span> <span data-ttu-id="31507-165">일괄 처리에 대한 트랜잭션이 실패하면 현재 일괄 처리에서 삽입한 내용만 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-165">If the transaction for any batch fails, only insertions from the current batch are rolled back.</span></span> <span data-ttu-id="31507-166">커밋된 트랜잭션으로 이미 가져온 일괄 처리는 나중에 발생한 오류의 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-166">Batches already imported by committed transactions are unaffected by a later failure.</span></span>  
  
 <span data-ttu-id="31507-167">이 옵션을 **-h "** ROWS_PER_BATCH \*\* = *`bb`* "\*\* 옵션과 함께 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="31507-167">Do not use this option in conjunction with the **-h"** ROWS_PER_BATCH **=*`bb`*"** option.</span></span>  
  
 `-c`  
 <span data-ttu-id="31507-168">문자 데이터 형식을 사용하여 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-168">Performs the operation using a character data type.</span></span> <span data-ttu-id="31507-169">이 옵션은 각 필드에 대해 묻지 않습니다. `char`접두사와 **\t** (탭 문자)를 필드 구분 기호로 사용 하지 않고 **\r\n** (줄 바꿈 문자)을 행 종결자로 사용 하 여을 저장소 유형으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-169">This option does not prompt for each field; it uses `char` as the storage type, without prefixes and with **\t** (tab character) as the field separator and **\r\n** (newline character) as the row terminator.</span></span> <span data-ttu-id="31507-170">`-c`는 `-w`와 호환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-170">`-c` is not compatible with `-w`.</span></span>  
  
 <span data-ttu-id="31507-171">자세한 내용은 [문자 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;](../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31507-171">For more information, see [Use Character Format to Import or Export Data &#40;SQL Server&#41;](../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="31507-172">**-C** { **ACP** | **OEM** | **RAW** | *code_page* }</span><span class="sxs-lookup"><span data-stu-id="31507-172">**-C** { **ACP** | **OEM** | **RAW** | *code_page* }</span></span>  
 <span data-ttu-id="31507-173">데이터 파일에서 데이터의 코드 페이지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-173">Specifies the code page of the data in the data file.</span></span> <span data-ttu-id="31507-174">*code_page* 는 `char` `varchar` `text` 문자 값이 127 보다 크거나 32 보다 작은, 또는 열이 데이터에 포함 되어 있는 경우에만 해당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-174">*code_page* is relevant only if the data contains `char`, `varchar`, or `text` columns with character values greater than 127 or less than 32.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="31507-175">서식 파일의 각 열에 대해 데이터 정렬 이름을 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-175">We recommend specifying a collation name for each column in a format file.</span></span>  
  
|<span data-ttu-id="31507-176">코드 페이지 값</span><span class="sxs-lookup"><span data-stu-id="31507-176">Code page value</span></span>|<span data-ttu-id="31507-177">Description</span><span class="sxs-lookup"><span data-stu-id="31507-177">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="31507-178">ACP</span><span class="sxs-lookup"><span data-stu-id="31507-178">ACP</span></span>|[!INCLUDE[vcpransi](../includes/vcpransi-md.md)]<span data-ttu-id="31507-179">/Microsoft Windows(ISO 1252)입니다.</span><span class="sxs-lookup"><span data-stu-id="31507-179">/Microsoft Windows (ISO 1252).</span></span>|  
|<span data-ttu-id="31507-180">OEM</span><span class="sxs-lookup"><span data-stu-id="31507-180">OEM</span></span>|<span data-ttu-id="31507-181">클라이언트가 사용하는 기본 코드 페이지입니다.</span><span class="sxs-lookup"><span data-stu-id="31507-181">Default code page used by the client.</span></span> <span data-ttu-id="31507-182">**-C** 를 지정하지 않은 경우 사용되는 기본 코드 페이지입니다.</span><span class="sxs-lookup"><span data-stu-id="31507-182">This is the default code page used if **-C** is not specified.</span></span>|  
|<span data-ttu-id="31507-183">RAW</span><span class="sxs-lookup"><span data-stu-id="31507-183">RAW</span></span>|<span data-ttu-id="31507-184">코드 페이지 간 변환이 일어나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-184">No conversion from one code page to another occurs.</span></span> <span data-ttu-id="31507-185">변환이 일어나지 않으므로 가장 빠른 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="31507-185">This is the fastest option because no conversion occurs.</span></span>|  
|<span data-ttu-id="31507-186">*code_page*</span><span class="sxs-lookup"><span data-stu-id="31507-186">*code_page*</span></span>|<span data-ttu-id="31507-187">850과 같은 특정 코드 페이지 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="31507-187">Specific code page number; for example, 850.</span></span><br /><br /> <span data-ttu-id="31507-188">**&#42;&#42; 중요 &#42;&#42;** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 는 코드 페이지 65001 (UTF-8 인코딩)을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-188">**&#42;&#42; Important &#42;&#42;** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] does not support code page 65001 (UTF-8 encoding).</span></span>|  
  
 <span data-ttu-id="31507-189">`-d`*database_name*</span><span class="sxs-lookup"><span data-stu-id="31507-189">`-d` *database_name*</span></span>  
 <span data-ttu-id="31507-190">연결할 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-190">Specifies the database to connect to.</span></span> <span data-ttu-id="31507-191">bcp.exe는 기본적으로 사용자의 기본 데이터베이스에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-191">By default, bcp.exe connects to the user's default database.</span></span> <span data-ttu-id="31507-192">`-d` *Database_name* 와 세 부분으로 구성 된 이름 (bcp.exe의 첫 번째 매개 변수로 전달 된*database_name*)을 지정 하면 데이터베이스 이름을 두 번 지정할 수 없으므로 오류가 발생 합니다. *Database_name* 하이픈 (-) 또는 슬래시 (/)로 시작 하는 경우와 데이터베이스 이름 사이에 공백을 추가 하지 마십시오 `-d` .</span><span class="sxs-lookup"><span data-stu-id="31507-192">If `-d`*database_name* and a three part name (*database_name.schema.table*, passed as the first parameter to bcp.exe) is specified, an error will occur because you cannot specify the database name twice.If *database_name* begins with a hyphen (-) or a forward slash (/), do not add a space between `-d` and the database name.</span></span>  
  
 <span data-ttu-id="31507-193">**-e** _err_file_</span><span class="sxs-lookup"><span data-stu-id="31507-193">**-e** _err_file_</span></span>  
 <span data-ttu-id="31507-194">**bcp** 유틸리티가 파일에서 데이터베이스로 전송할 수 없는 행을 저장하는 데 사용되는 오류 파일의 전체 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-194">Specifies the full path of an error file used to store any rows that the **bcp** utility cannot transfer from the file to the database.</span></span> <span data-ttu-id="31507-195">**bcp** 명령의 오류 메시지는 사용자의 워크스테이션에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="31507-195">Error messages from the **bcp** command go to the workstation of the user.</span></span> <span data-ttu-id="31507-196">이 옵션을 사용하지 않으면 오류 파일이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-196">If this option is not used, an error file is not created.</span></span>  
  
 <span data-ttu-id="31507-197">*err_file* 이 하이픈(-) 또는 슬래시(/)로 시작하는 경우에는 **-e** 와 *err_file* 값 사이에 공백을 포함하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="31507-197">If *err_file* begins with a hyphen (-) or a forward slash (/), do not include a space between **-e** and the *err_file* value.</span></span>  
  
 <span data-ttu-id="31507-198">**-E**</span><span class="sxs-lookup"><span data-stu-id="31507-198">**-E**</span></span>  
 <span data-ttu-id="31507-199">가져온 데이터 파일의 ID 값이 ID 열에 사용되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-199">Specifies that identity value or values in the imported data file are to be used for the identity column.</span></span> <span data-ttu-id="31507-200">**-E** 를 지정하지 않으면 가져오는 데이터 파일에 있는 이 열의 ID 값이 무시되고 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서 테이블을 만들 때 지정한 초기값 및 증가값을 기반으로 고유 값을 자동으로 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-200">If **-E** is not given, the identity values for this column in the data file being imported are ignored, and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] automatically assigns unique values based on the seed and increment values specified during table creation.</span></span>  
  
 <span data-ttu-id="31507-201">데이터 파일에 테이블이나 뷰의 ID 열 값이 포함되지 않은 경우 서식 파일을 사용하여 데이터를 가져올 때 테이블이나 뷰의 ID 열을 생략하도록 지정합니다. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서 해당 열에 자동으로 고유 값을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-201">If the data file does not contain values for the identity column in the table or view, use a format file to specify that the identity column in the table or view should be skipped when importing data; [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] automatically assigns unique values for the column.</span></span> <span data-ttu-id="31507-202">자세한 내용은 [DBCC CHECKIDENT&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkident-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31507-202">For more information, see [DBCC CHECKIDENT &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkident-transact-sql).</span></span>  
  
 <span data-ttu-id="31507-203">**-E** 옵션을 사용하려면 특별한 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-203">The **-E** option has a special permissions requirement.</span></span> <span data-ttu-id="31507-204">자세한 내용은 이 항목의 뒷부분에 나오는 "주의"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="31507-204">For more information, see "Remarks" later in this topic.</span></span>  
  
 <span data-ttu-id="31507-205">**-f** _format_file_</span><span class="sxs-lookup"><span data-stu-id="31507-205">**-f** _format_file_</span></span>  
 <span data-ttu-id="31507-206">서식 파일의 전체 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-206">Specifies the full path of a format file.</span></span> <span data-ttu-id="31507-207">다음과 같이 이 옵션의 의미는 해당 환경에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="31507-207">The meaning of this option depends on the environment in which it is used, as follows:</span></span>  
  
-   <span data-ttu-id="31507-208">**format** 옵션과 함께 **-f** 를 사용하는 경우 지정한 테이블 또는 뷰에 대해 지정한 *format_file* 이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="31507-208">If **-f** is used with the **format** option, the specified *format_file* is created for the specified table or view.</span></span> <span data-ttu-id="31507-209">XML 서식 파일을 만들려면 **-x** 옵션도 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-209">To create an XML format file, also specify the **-x** option.</span></span> <span data-ttu-id="31507-210">자세한 내용은 [서식 파일 만들기&#40;SQL Server&#41;](../relational-databases/import-export/create-a-format-file-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31507-210">For more information, see [Create a Format File &#40;SQL Server&#41;](../relational-databases/import-export/create-a-format-file-sql-server.md).</span></span>  
  
-   <span data-ttu-id="31507-211">**-f** 를 **in** 또는 **out** 옵션과 함께 사용하는 경우 기존 서식 파일이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-211">If used with the **in** or **out** option, **-f** requires an existing format file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="31507-212">원할 경우 **in** 또는 **out** 옵션과 함께 서식 파일을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-212">Using a format file in with the **in** or **out** option is optional.</span></span> <span data-ttu-id="31507-213">- **F** 옵션이 없을 경우 **-n**, `-c` , `-w` 또는 **-n** 을 지정 하지 않으면 명령에서 형식 정보를 묻는 메시지를 표시 하 고 응답을 서식 파일에 저장할 수 있습니다 (기본 파일 이름은 Bcp. fmt).</span><span class="sxs-lookup"><span data-stu-id="31507-213">In the absence of the **-f** option, if **-n**, `-c`, `-w`, or **-N** is not specified, the command prompts for format information and lets you save your responses in a format file (whose default file name is Bcp.fmt).</span></span>  
  
 <span data-ttu-id="31507-214">*format_file* 이 하이픈(-) 또는 슬래시(/)로 시작하는 경우에는 **-f** 와 *format_file* 값 사이에 공백을 포함하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="31507-214">If *format_file* begins with a hyphen (-) or a forward slash (/), do not include a space between **-f** and the *format_file* value.</span></span>  
  
 <span data-ttu-id="31507-215">**-F** _first_row_</span><span class="sxs-lookup"><span data-stu-id="31507-215">**-F** _first_row_</span></span>  
 <span data-ttu-id="31507-216">테이블에서 내보내거나 데이터 파일에서 가져올 첫 번째 행 번호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-216">Specifies the number of the first row to export from a table or import from a data file.</span></span> <span data-ttu-id="31507-217">이 매개 변수에는 (>) 0 보다 크고 () 보다 작거나 ( \< =) 총 행 수와 같은 값이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-217">This parameter requires a value greater than (>) 0 but less than (\<) or equal to (=) the total number rows.</span></span> <span data-ttu-id="31507-218">이 매개 변수를 지정하지 않을 경우 기본값은 파일의 첫 번째 행입니다.</span><span class="sxs-lookup"><span data-stu-id="31507-218">In the absence of this parameter, the default is the first row of the file.</span></span>  
  
 <span data-ttu-id="31507-219">*first_row* 는 최대 2^63-1의 값을 갖는 양의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="31507-219">*first_row* can be a positive integer with a value up to 2^63-1.</span></span> <span data-ttu-id="31507-220">**-F**_first_row_는 1부터 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-220">**-F**_first_row_ is 1-based.</span></span>  
  
 <span data-ttu-id="31507-221">**-h"** _hint_[ **,**... *n*] **"**</span><span class="sxs-lookup"><span data-stu-id="31507-221">**-h"** _hint_[ **,**... *n*] **"**</span></span>  
 <span data-ttu-id="31507-222">데이터를 테이블 또는 뷰로 대량으로 가져올 때 사용할 힌트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-222">Specifies the hint or hints to be used during a bulk import of data into a table or view.</span></span>  
  
 <span data-ttu-id="31507-223">ORDER **(**_column_[ASC | DESC] [**,**... *n*] **)**</span><span class="sxs-lookup"><span data-stu-id="31507-223">ORDER **(**_column_[ASC | DESC] [**,**...*n*]**)**</span></span>  
 <span data-ttu-id="31507-224">데이터 파일에 있는 데이터의 정렬 순서입니다.</span><span class="sxs-lookup"><span data-stu-id="31507-224">The sort order of the data in the data file.</span></span> <span data-ttu-id="31507-225">가져올 데이터를 테이블의 클러스터형 인덱스(있는 경우)에 따라 정렬하면 대량 가져오기 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-225">Bulk import performance is improved if the data being imported is sorted according to the clustered index on the table, if any.</span></span> <span data-ttu-id="31507-226">데이터 파일을 클러스터형 인덱스 키와 다른 순서로 정렬하거나 테이블에 클러스터형 인덱스가 없으면 ORDER 절이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-226">If the data file is sorted in a different order, that is other than the order of a clustered index key, or if there is no clustered index on the table, the ORDER clause is ignored.</span></span> <span data-ttu-id="31507-227">지정한 열 이름은 대상 테이블에서 올바른 열 이름이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-227">The column names supplied must be valid column names in the destination table.</span></span> <span data-ttu-id="31507-228">기본적으로 **bcp** 는 데이터 파일이 정렬되지 않은 것으로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-228">By default, **bcp** assumes the data file is unordered.</span></span> <span data-ttu-id="31507-229">대량 가져오기 작업을 최적화하기 위해 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서는 가져온 데이터가 정렬되어 있는지도 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-229">For optimized bulk import, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] also validates that the imported data is sorted.</span></span>  
  
 <span data-ttu-id="31507-230">ROWS_PER_BATCH **=** _bb_</span><span class="sxs-lookup"><span data-stu-id="31507-230">ROWS_PER_BATCH **=**_bb_</span></span>  
 <span data-ttu-id="31507-231">일괄 처리당 데이터 행 수( *bb*)입니다.</span><span class="sxs-lookup"><span data-stu-id="31507-231">Number of rows of data per batch (as *bb*).</span></span> <span data-ttu-id="31507-232">**-b** 를 지정하지 않은 경우에 사용되며 전체 데이터 파일을 단일 트랜잭션으로 서버에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="31507-232">Used when **-b** is not specified, resulting in the entire data file being sent to the server as a single transaction.</span></span> <span data-ttu-id="31507-233">서버는 *bb*값에 따라 대량 로드를 최적화합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-233">The server optimizes the bulk load according to the value *bb*.</span></span> <span data-ttu-id="31507-234">기본적으로 ROWS_PER_BATCH는 알 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-234">By default, ROWS_PER_BATCH is unknown.</span></span>  
  
 <span data-ttu-id="31507-235">KILOBYTES_PER_BATCH **=** _참조_</span><span class="sxs-lookup"><span data-stu-id="31507-235">KILOBYTES_PER_BATCH **=** _cc_</span></span>  
 <span data-ttu-id="31507-236">일괄 처리당 데이터의 대략적인 KB 단위 크기( *cc*)입니다.</span><span class="sxs-lookup"><span data-stu-id="31507-236">Approximate number of kilobytes of data per batch (as *cc*).</span></span> <span data-ttu-id="31507-237">기본적으로 KILOBYTES_PER_BATCH는 알 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-237">By default, KILOBYTES_PER_BATCH is unknown.</span></span>  
  
 <span data-ttu-id="31507-238">TABLOCK</span><span class="sxs-lookup"><span data-stu-id="31507-238">TABLOCK</span></span>  
 <span data-ttu-id="31507-239">대량 로드 작업이 진행되는 동안 대량 업데이트 테이블 수준 잠금이 사용되도록 지정합니다. 그렇지 않으면 행 수준 잠금이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-239">Specifies that a bulk update table-level lock is acquired for the duration of the bulk load operation; otherwise, a row-level lock is acquired.</span></span> <span data-ttu-id="31507-240">대량 복사 작업 중에 잠금을 보유하면 테이블의 잠금 경합이 줄어들기 때문에 이 힌트를 사용하면 성능이 크게 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-240">This hint significantly improves performance because holding a lock for the duration of the bulk-copy operation reduces lock contention on the table.</span></span> <span data-ttu-id="31507-241">테이블에 인덱스가 없고 **TABLOCK** 이 지정되어 있으면 여러 클라이언트가 동시에 테이블을 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-241">A table can be loaded concurrently by multiple clients if the table has no indexes and **TABLOCK** is specified.</span></span> <span data-ttu-id="31507-242">기본적으로 잠금 동작은 **table lock on bulk load**테이블 옵션에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-242">By default, locking behavior is determined by the table option **table lock on bulk load**.</span></span>  
  
 <span data-ttu-id="31507-243">CHECK_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="31507-243">CHECK_CONSTRAINTS</span></span>  
 <span data-ttu-id="31507-244">대량 가져오기 작업 중 대상 테이블 또는 뷰의 모든 제약 조건을 검사하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-244">Specifies that all constraints on the target table or view must be checked during the bulk-import operation.</span></span> <span data-ttu-id="31507-245">CHECK_CONSTRAINTS 힌트를 지정하지 않으면 모든 CHECK 및 FOREIGN KEY 제약 조건이 무시되며 작업 후 테이블의 제약 조건은 트러스트되지 않는 것으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-245">Without the CHECK_CONSTRAINTS hint, any CHECK and FOREIGN KEY constraints are ignored, and after the operation the constraint on the table is marked as not-trusted.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="31507-246">UNIQUE, PRIMARY KEY 및 NOT NULL 제약 조건은 항상 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-246">UNIQUE, PRIMARY KEY, and NOT NULL constraints are always enforced.</span></span>  
  
 <span data-ttu-id="31507-247">어느 시점에서는 전체 테이블의 제약 조건을 확인할 필요가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-247">At some point, you will need to check the constraints on the entire table.</span></span> <span data-ttu-id="31507-248">대량 가져오기 작업을 수행하기 전에 테이블이 비어 있지 않은 경우 제약 조건의 유효성을 다시 검사하는 비용이 증분 데이터에 CHECK 제약 조건을 적용하는 비용을 초과할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-248">If the table was nonempty before the bulk import operation, the cost of revalidating the constraint may exceed the cost of applying CHECK constraints to the incremental data.</span></span> <span data-ttu-id="31507-249">따라서 일반적으로 증분 대량 가져오기 중에 제약 조건을 검사하도록 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-249">Therefore, we recommend that normally you enable constraint checking during an incremental bulk import.</span></span>  
  
 <span data-ttu-id="31507-250">입력 데이터에 제약 조건을 위반하는 행이 포함된 경우에는 제약 조건을 사용하지 않을 수 있습니다(기본 동작).</span><span class="sxs-lookup"><span data-stu-id="31507-250">A situation in which you might want constraints disabled (the default behavior) is if the input data contains rows that violate constraints.</span></span> <span data-ttu-id="31507-251">CHECK 제약 조건을 사용하지 않으면 데이터를 가져온 다음 [!INCLUDE[tsql](../includes/tsql-md.md)] 문을 사용하여 잘못된 데이터를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-251">With CHECK constraints disabled, you can import the data and then use [!INCLUDE[tsql](../includes/tsql-md.md)] statements to remove data that is not valid.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="31507-252">**bcp** 는 이제 데이터 유효성 검사 및 데이터 검사를 강제로 실행하므로 스크립트를 데이터 파일의 잘못된 데이터에 대해 실행할 경우 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-252">**bcp** now enforces data validation and data checks that might cause scripts to fail if they are executed on invalid data in a data file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="31507-253">**-m** _max_errors_ 스위치는 제약 조건 검사에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-253">The **-m** _max_errors_ switch does not apply to constraint checking.</span></span>  
  
 <span data-ttu-id="31507-254">FIRE_TRIGGERS</span><span class="sxs-lookup"><span data-stu-id="31507-254">FIRE_TRIGGERS</span></span>  
 <span data-ttu-id="31507-255">**in** 인수와 함께 지정하면 대량 복사 작업 중에 대상 테이블에 정의한 삽입 트리거가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-255">Specified with the **in** argument, any insert triggers defined on the destination table will run during the bulk-copy operation.</span></span> <span data-ttu-id="31507-256">FIRE_TRIGGERS를 지정하지 않으면 삽입 트리거가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-256">If FIRE_TRIGGERS is not specified, no insert triggers will run.</span></span> <span data-ttu-id="31507-257">FIRE_TRIGGERS는 **out**, **queryout**및 **format** 인수에 대해 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-257">FIRE_TRIGGERS is ignored for the **out**, **queryout**, and **format** arguments.</span></span>  
  
 <span data-ttu-id="31507-258">**-i** _input_file_</span><span class="sxs-lookup"><span data-stu-id="31507-258">**-i** _input_file_</span></span>  
 <span data-ttu-id="31507-259">대화형 모드를 사용 하 여 대량 복사를 수행할 때 각 데이터 필드에 대 한 명령 프롬프트 질문에 대 한 응답을 포함 하는 지시 파일의 이름을 지정 합니다 (**-n**, `-c` , `-w` 또는 **-n** 을 지정 하지 않음).</span><span class="sxs-lookup"><span data-stu-id="31507-259">Specifies the name of a response file, containing the responses to the command prompt questions for each data field when a bulk copy is being performed using interactive mode (**-n**, `-c`, `-w`, or **-N** not specified).</span></span>  
  
 <span data-ttu-id="31507-260">*input_file* 이 하이픈(-) 또는 슬래시(/)로 시작하는 경우에는 **-i** 와 *input_file* 값 사이에 공백을 포함하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="31507-260">If *input_file* begins with a hyphen (-) or a forward slash (/), do not include a space between **-i** and the *input_file* value.</span></span>  
  
 <span data-ttu-id="31507-261">**-k**</span><span class="sxs-lookup"><span data-stu-id="31507-261">**-k**</span></span>  
 <span data-ttu-id="31507-262">작업 시 삽입된 열에 기본값이 지정되지 않고 빈 열이 Null 값을 보유하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-262">Specifies that empty columns should retain a null value during the operation, rather than have any default values for the columns inserted.</span></span> <span data-ttu-id="31507-263">자세한 내용은 [대량 가져오기 수행 중 Null 유지 또는 기본값 사용&#40;SQL Server&#41;](../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31507-263">For more information, see [Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;](../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md).</span></span>  
  
 <span data-ttu-id="31507-264">**-K** _application_intent_</span><span class="sxs-lookup"><span data-stu-id="31507-264">**-K** _application_intent_</span></span>  
 <span data-ttu-id="31507-265">서버에 연결할 때 애플리케이션 작업 유형을 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-265">Declares the application workload type when connecting to a server.</span></span> <span data-ttu-id="31507-266">**ReadOnly**값만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-266">The only value that is possible is **ReadOnly**.</span></span> <span data-ttu-id="31507-267">**-K**를 지정하지 않으면 bcp 유틸리티가 AlwaysOn 가용성 그룹에 있는 보조 복제본에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-267">If **-K** is not specified, the bcp utility will not support connectivity to a secondary replica in an AlwaysOn availability group.</span></span> <span data-ttu-id="31507-268">자세한 내용은 [활성 보조: 읽기 가능한 보조 복제본 (AlwaysOn 가용성 그룹)](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="31507-268">For more information, see [Active Secondaries: Readable Secondary Replicas (AlwaysOn Availability Groups)](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="31507-269">**-L** _last_row_</span><span class="sxs-lookup"><span data-stu-id="31507-269">**-L** _last_row_</span></span>  
 <span data-ttu-id="31507-270">테이블에서 내보내거나 데이터 파일에서 가져올 마지막 행 번호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-270">Specifies the number of the last row to export from a table or import from a data file.</span></span> <span data-ttu-id="31507-271">이 매개 변수에는 (>) 0 보다 크고 () 보다 작거나 ( \< =) 마지막 행 번호 보다 작거나 같은 값이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-271">This parameter requires a value greater than (>) 0 but less than (\<) or equal to (=) the number of the last row.</span></span> <span data-ttu-id="31507-272">이 매개 변수를 지정하지 않을 경우 기본값은 파일의 마지막 행입니다.</span><span class="sxs-lookup"><span data-stu-id="31507-272">In the absence of this parameter, the default is the last row of the file.</span></span>  
  
 <span data-ttu-id="31507-273">*last_row* 는 최대 2^63-1의 값을 갖는 양의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="31507-273">*last_row* can be a positive integer with a value up to 2^63-1.</span></span>  
  
 <span data-ttu-id="31507-274">**-m** _max_errors_</span><span class="sxs-lookup"><span data-stu-id="31507-274">**-m** _max_errors_</span></span>  
 <span data-ttu-id="31507-275">**bcp** 작업이 취소되는 최대 구문 오류 발생 횟수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-275">Specifies the maximum number of syntax errors that can occur before the **bcp** operation is canceled.</span></span> <span data-ttu-id="31507-276">구문 오류란 대상 데이터 형식으로의 데이터 변환 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="31507-276">A syntax error implies a data conversion error to the target data type.</span></span> <span data-ttu-id="31507-277">총 *max_errors* 수에는 제약 조건 위반과 같이 서버에서만 검색할 수 있는 오류는 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-277">The *max_errors* total excludes any errors that can be detected only at the server, such as constraint violations.</span></span>  
  
 <span data-ttu-id="31507-278">**bcp** 유틸리티가 복사할 수 없는 행은 무시되며 오류가 하나 발생한 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-278">A row that cannot be copied by the **bcp** utility is ignored and is counted as one error.</span></span> <span data-ttu-id="31507-279">이 옵션을 지정하지 않은 경우의 기본값은 10입니다.</span><span class="sxs-lookup"><span data-stu-id="31507-279">If this option is not included, the default is 10.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="31507-280">**-M** 옵션은 `money` 또는 데이터 형식을 변환 하는 데에도 적용 되지 않습니다 `bigint` .</span><span class="sxs-lookup"><span data-stu-id="31507-280">The **-m** option also does not apply to converting the `money` or `bigint` data types.</span></span>  
  
 <span data-ttu-id="31507-281">**-n**</span><span class="sxs-lookup"><span data-stu-id="31507-281">**-n**</span></span>  
 <span data-ttu-id="31507-282">데이터의 네이티브(데이터베이스) 데이터 형식을 사용하여 대량 복사 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-282">Performs the bulk-copy operation using the native (database) data types of the data.</span></span> <span data-ttu-id="31507-283">이 옵션이 필드마다 표시되지는 않습니다. 이 옵션은 네이티브 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-283">This option does not prompt for each field; it uses the native values.</span></span>  
  
 <span data-ttu-id="31507-284">자세한 내용은 [네이티브 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;](../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31507-284">For more information, see [Use Native Format to Import or Export Data &#40;SQL Server&#41;](../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="31507-285">**-N**</span><span class="sxs-lookup"><span data-stu-id="31507-285">**-N**</span></span>  
 <span data-ttu-id="31507-286">문자가 아닌 데이터의 경우 데이터의 네이티브(데이터베이스) 데이터 형식을 사용하고 문자 데이터의 경우 유니코드 문자를 사용하여 대량 복사 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-286">Performs the bulk-copy operation using the native (database) data types of the data for noncharacter data, and Unicode characters for character data.</span></span> <span data-ttu-id="31507-287">이 옵션은 `-w` 옵션을 사용할 때보다 성능이 높으며 데이터 파일을 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스 간에 데이터를 전송할 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-287">This option offers a higher performance alternative to the `-w` option, and is intended for transferring data from one instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to another using a data file.</span></span> <span data-ttu-id="31507-288">이 옵션은 각 필드에 대한 정보를 요청하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-288">It does not prompt for each field.</span></span> <span data-ttu-id="31507-289">ANSI 확장 문자가 들어 있는 데이터를 전송하는 경우 기본 모드의 성능을 활용하려고 할 때 이 옵션을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="31507-289">Use this option when you are transferring data that contains ANSI extended characters and you want to take advantage of the performance of native mode.</span></span>  
  
 <span data-ttu-id="31507-290">자세한 내용은 [유니코드 네이티브 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;](../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31507-290">For more information, see [Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;](../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="31507-291">**-N**과 함께 bcp.exe를 사용 하 여 동일한 테이블 스키마에 데이터를 내보낸 다음 가져올 경우 비유니코드 고정 길이 문자 열 (예:)이 있으면 잘림 경고가 표시 될 수 있습니다 `char(10)` .</span><span class="sxs-lookup"><span data-stu-id="31507-291">If you export and then import data to the same table schema by using bcp.exe with **-N**, you might see a truncation warning if there is a fixed length, non-Unicode character column (for example, `char(10)`).</span></span>  
  
 <span data-ttu-id="31507-292">이 경고는 무시해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-292">The warning can be ignored.</span></span> <span data-ttu-id="31507-293">**-N** 대신 **-n**을 사용하여 이 경고를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-293">One way to resolve this warning is to use **-n** instead of **-N**.</span></span>  
  
 <span data-ttu-id="31507-294">**-o** _output_file_</span><span class="sxs-lookup"><span data-stu-id="31507-294">**-o** _output_file_</span></span>  
 <span data-ttu-id="31507-295">명령 프롬프트에서 리디렉션된 출력을 받는 파일의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-295">Specifies the name of a file that receives output redirected from the command prompt.</span></span>  
  
 <span data-ttu-id="31507-296">*output_file* 이 하이픈(-) 또는 슬래시(/)로 시작하는 경우에는 **-o** 와 *output_file* 값 사이에 공백을 포함하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="31507-296">If *output_file* begins with a hyphen (-) or a forward slash (/), do not include a space between **-o** and the *output_file* value.</span></span>  
  
 <span data-ttu-id="31507-297">**-P** _password_</span><span class="sxs-lookup"><span data-stu-id="31507-297">**-P** _password_</span></span>  
 <span data-ttu-id="31507-298">로그인 ID의 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-298">Specifies the password for the login ID.</span></span> <span data-ttu-id="31507-299">이 옵션을 사용하지 않으면 **bcp** 명령을 실행하는 동안 암호를 묻는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-299">If this option is not used, the **bcp** command prompts for a password.</span></span> <span data-ttu-id="31507-300">암호를 입력하지 않고 명령 프롬프트의 마지막에 이 옵션을 사용하면 **bcp** 는 기본 암호 NULL을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-300">If this option is used at the end of the command prompt without a password, **bcp** uses the default password (NULL).</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../includes/ssnotestrongpass-md.md)]  
  
 <span data-ttu-id="31507-301">암호를 마스킹하려면 **-U** 옵션과 함께 **-P** 옵션을 지정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="31507-301">To mask your password, do not specify the **-P** option along with the **-U** option.</span></span> <span data-ttu-id="31507-302">대신 **-U** 옵션 및 기타 스위치와 함께 **bcp** 를 지정하고( **-P**는 지정하지 않음) Enter 키를 누르면 암호를 묻는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-302">Instead, after specifying **bcp** along with the **-U** option and other switches (do not specify **-P**), press ENTER, and the command will prompt you for a password.</span></span> <span data-ttu-id="31507-303">이 방법을 사용하면 암호 입력 시 암호가 마스킹됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-303">This method ensures that your password will be masked when it is entered.</span></span>  
  
 <span data-ttu-id="31507-304">*password* 가 하이픈(-) 또는 슬래시(/)로 시작하는 경우에는 **-P** 와 *password* 값 사이에 공백을 포함하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="31507-304">If *password* begins with a hyphen (-) or a forward slash (/), do not add a space between **-P** and the *password* value.</span></span>  
  
 `-q`  
 <span data-ttu-id="31507-305">**bcp** 유틸리티와 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스 간의 연결에서 SET QUOTED_IDENTIFIERS ON 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-305">Executes the SET QUOTED_IDENTIFIERS ON statement in the connection between the **bcp** utility and an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="31507-306">이 옵션을 사용하여 공백이나 작은따옴표를 포함하는 데이터베이스, 소유자, 테이블 또는 뷰 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-306">Use this option to specify a database, owner, table, or view name that contains a space or a single quotation mark.</span></span> <span data-ttu-id="31507-307">세 부분으로 구성된 테이블 이름이나 뷰 이름 전체를 큰따옴표("")로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-307">Enclose the entire three-part table or view name in quotation marks ("").</span></span>  
  
 <span data-ttu-id="31507-308">공백이나 작은따옴표가 들어 있는 데이터베이스 이름을 지정하려면 **–q** 옵션을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-308">To specify a database name that contains a space or single quotation mark, you must use the **-q** option.</span></span>  
  
 <span data-ttu-id="31507-309">`-q`는 `-d`로 전달된 값에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-309">`-q` does not apply to values passed to `-d`.</span></span>  
  
 <span data-ttu-id="31507-310">자세한 내용은 이 항목의 뒷부분에 나오는 주의를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="31507-310">For more information, see Remarks, later in this topic.</span></span>  
  
 <span data-ttu-id="31507-311">**-r** _row_term_</span><span class="sxs-lookup"><span data-stu-id="31507-311">**-r** _row_term_</span></span>  
 <span data-ttu-id="31507-312">행 종결자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-312">Specifies the row terminator.</span></span> <span data-ttu-id="31507-313">기본값은 **\n** (줄 바꿈 문자)입니다.</span><span class="sxs-lookup"><span data-stu-id="31507-313">The default is **\n** (newline character).</span></span> <span data-ttu-id="31507-314">기본 행 종결자를 재정의하려면 이 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-314">Use this parameter to override the default row terminator.</span></span> <span data-ttu-id="31507-315">자세한 내용은 [필드 및 행 종결자 지정&#40;SQL Server&#41;](../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31507-315">For more information, see [Specify Field and Row Terminators &#40;SQL Server&#41;](../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md).</span></span>  
  
 <span data-ttu-id="31507-316">bcp.exe 명령에서 16진수 표기법으로 행 종료 문자를 지정하는 경우 값은 0x00에서 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="31507-316">If you specify the row terminator in hexadecimal notation in a bcp.exe command, the value will be truncated at 0x00.</span></span> <span data-ttu-id="31507-317">예를 들어 0x410041을 지정하면 0x41이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-317">For example, if you specify 0x410041, 0x41 will be used.</span></span>  
  
 <span data-ttu-id="31507-318">*row_term* 이 하이픈(-) 또는 슬래시(/)로 시작하는 경우에는 **-r** 과 *row_term* 값 사이에 공백을 포함하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="31507-318">If *row_term* begins with a hyphen (-) or a forward slash (/), do not include a space between **-r** and the *row_term* value.</span></span>  
  
 <span data-ttu-id="31507-319">**-R**</span><span class="sxs-lookup"><span data-stu-id="31507-319">**-R**</span></span>  
 <span data-ttu-id="31507-320">클라이언트 컴퓨터의 로캘 설정에 정의된 국가별 형식을 사용하여 통화, 날짜 및 시간 데이터를 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 로 대량 복사하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-320">Specifies that currency, date, and time data is bulk copied into [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] using the regional format defined for the locale setting of the client computer.</span></span> <span data-ttu-id="31507-321">기본적으로 국가별 설정은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-321">By default, regional settings are ignored.</span></span>  
  
 <span data-ttu-id="31507-322">**-S** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="31507-322">**-S** _server_name_[ **\\**_instance_name_]</span></span>  
 <span data-ttu-id="31507-323">연결할 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-323">Specifies the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to which to connect.</span></span> <span data-ttu-id="31507-324">서버를 지정하지 않으면 **bcp** 유틸리티가 로컬 컴퓨터에 있는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 기본 인스턴스에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-324">If no server is specified, the **bcp** utility connects to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the local computer.</span></span> <span data-ttu-id="31507-325">네트워크의 원격 컴퓨터나 명명된 로컬 인스턴스에서 **bcp** 명령을 실행할 때 이 옵션을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-325">This option is required when a **bcp** command is run from a remote computer on the network or a local named instance.</span></span> <span data-ttu-id="31507-326">서버에 있는 기본 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 연결하려면 *server_name*만 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-326">To connect to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on a server, specify only *server_name*.</span></span> <span data-ttu-id="31507-327">의 명명 된 인스턴스에 연결 하려면 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] *server_name **_\\_** instance_name*를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-327">To connect to a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], specify *server_name\*\*_\\_*\* instance_name\*.</span></span>  
  
 <span data-ttu-id="31507-328">`-t`*field_term*</span><span class="sxs-lookup"><span data-stu-id="31507-328">`-t` *field_term*</span></span>  
 <span data-ttu-id="31507-329">필드 종결자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-329">Specifies the field terminator.</span></span> <span data-ttu-id="31507-330">기본값은 **\t** (탭 문자)입니다.</span><span class="sxs-lookup"><span data-stu-id="31507-330">The default is **\t** (tab character).</span></span> <span data-ttu-id="31507-331">기본 필드 종결자를 재정의하려면 이 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-331">Use this parameter to override the default field terminator.</span></span> <span data-ttu-id="31507-332">자세한 내용은 [필드 및 행 종결자 지정&#40;SQL Server&#41;](../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31507-332">For more information, see [Specify Field and Row Terminators &#40;SQL Server&#41;](../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md).</span></span>  
  
 <span data-ttu-id="31507-333">bcp.exe 명령에서 16진수 표기법으로 필드 종결자를 지정하는 경우 값은 0x00에서 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="31507-333">If you specify the field terminator in hexadecimal notation in a bcp.exe command, the value will be truncated at 0x00.</span></span> <span data-ttu-id="31507-334">예를 들어 0x410041을 지정하면 0x41이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-334">For example, if you specify 0x410041, 0x41 will be used.</span></span>  
  
 <span data-ttu-id="31507-335">*Field_term* 하이픈 (-) 또는 슬래시 (/)로 시작 하는 경우 `-t` 와 *field_term* 값 사이에 공백을 포함 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="31507-335">If *field_term* begins with a hyphen (-) or a forward slash (/), do not include a space between `-t` and the *field_term* value.</span></span>  
  
 <span data-ttu-id="31507-336">**-T**</span><span class="sxs-lookup"><span data-stu-id="31507-336">**-T**</span></span>  
 <span data-ttu-id="31507-337">**bcp** 유틸리티가 통합 보안을 사용하는 트러스트된 연결을 통해 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 로 연결되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-337">Specifies that the **bcp** utility connects to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] with a trusted connection using integrated security.</span></span> <span data-ttu-id="31507-338">네트워크 사용자의 보안 자격 증명, *login_id*및 *password* 는 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-338">The security credentials of the network user, *login_id*, and *password* are not required.</span></span> <span data-ttu-id="31507-339">**-T** 를 지정하지 않은 경우 성공적으로 로그인하려면 **-U** 와 **-P** 를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-339">If **-T** is not specified, you need to specify **-U** and **-P** to successfully log in.</span></span>  
  
 <span data-ttu-id="31507-340">**-U** _login_id_</span><span class="sxs-lookup"><span data-stu-id="31507-340">**-U** _login_id_</span></span>  
 <span data-ttu-id="31507-341">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]연결에 사용하는 로그인 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-341">Specifies the login ID used to connect to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="31507-342">**bcp** 유틸리티에서 통합 보안을 사용하는 트러스트된 연결을 통해 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에 연결하는 경우 **사용자 이름** 과 *암호* 를 조합하여 사용하는 대신 *-T* 옵션(트러스트된 연결)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-342">When the **bcp** utility is connecting to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] with a trusted connection using integrated security, use the **-T** option (trusted connection) instead of the *user name* and *password* combination.</span></span>  
  
 <span data-ttu-id="31507-343">**-v**</span><span class="sxs-lookup"><span data-stu-id="31507-343">**-v**</span></span>  
 <span data-ttu-id="31507-344">**bcp** 유틸리티 버전 번호 및 저작권을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-344">Reports the **bcp** utility version number and copyright.</span></span>  
  
 <span data-ttu-id="31507-345">**-V** (**80** | **90** | **100**| **110**)</span><span class="sxs-lookup"><span data-stu-id="31507-345">**-V** (**80** | **90** | **100**| **110**)</span></span>  
 <span data-ttu-id="31507-346">이전 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]버전의 데이터 형식을 사용하여 대량 복사 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-346">Performs the bulk-copy operation using data types from an earlier version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="31507-347">이 옵션은 각 필드에 대한 정보를 요청하지 않으며 기본값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-347">This option does not prompt for each field; it uses the default values.</span></span>  
  
 <span data-ttu-id="31507-348">**80** = [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31507-348">**80** = [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)]</span></span>  
  
 <span data-ttu-id="31507-349">**90** = [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31507-349">**90** = [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]</span></span>  
  
 <span data-ttu-id="31507-350">**100** = [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 및 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31507-350">**100** = [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] and [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]</span></span>  
  
 <span data-ttu-id="31507-351">**110 =[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="31507-351">**110 = [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]**</span></span>  
  
 <span data-ttu-id="31507-352">예를 들어 [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)]에서는 지원되지 않지만 그 이후 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]버전에 도입된 형식에 대한 데이터를 생성하려면 -V80 옵션을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="31507-352">For example, to generate data for types not supported by [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)], but were introduced in later versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], use the -V80 option.</span></span>  
  
 <span data-ttu-id="31507-353">자세한 내용은 [SQL Server 이전 버전으로부터 기본 및 문자 형식 데이터 가져오기](../relational-databases/import-export/import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31507-353">For more information, see [Import Native and Character Format Data from Earlier Versions of SQL Server](../relational-databases/import-export/import-native-and-character-format-data-from-earlier-versions-of-sql-server.md).</span></span>  
  
 `-w`  
 <span data-ttu-id="31507-354">유니코드 문자를 사용하여 대량 복사 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-354">Performs the bulk copy operation using Unicode characters.</span></span> <span data-ttu-id="31507-355">이 옵션은 각 필드에 대해 묻지 않습니다. `nchar`저장소 유형, 접두사, **\t** (탭 문자)를 필드 구분 기호로 사용 하 고 **\n** (줄 바꿈 문자)를 행 종결자로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-355">This option does not prompt for each field; it uses `nchar` as the storage type, no prefixes, **\t** (tab character) as the field separator, and **\n** (newline character) as the row terminator.</span></span> <span data-ttu-id="31507-356">`-w`는 `-c`와 호환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-356">`-w` is not compatible with `-c`.</span></span>  
  
 <span data-ttu-id="31507-357">자세한 내용은 [유니코드 문자 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;](../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31507-357">For more information, see [Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;](../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="31507-358">**-x**</span><span class="sxs-lookup"><span data-stu-id="31507-358">**-x**</span></span>  
 <span data-ttu-id="31507-359">**format** 및 **-f**_format_file_ 옵션과 함께 사용되며 기본 비 XML 서식 파일 대신 XML 기반 서식 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-359">Used with the **format** and **-f**_format_file_ options, generates an XML-based format file instead of the default non-XML format file.</span></span> <span data-ttu-id="31507-360">데이터를 가져오거나 내보낼 때 **-x** 는 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-360">The **-x** does not work when importing or exporting data.</span></span> <span data-ttu-id="31507-361">**format** 및 **-f**_format_file_을 함께 사용하지 않으면 오류가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-361">It generates an error if used without both **format** and **-f**_format_file_.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31507-362">설명</span><span class="sxs-lookup"><span data-stu-id="31507-362">Remarks</span></span>  
 <span data-ttu-id="31507-363">도구를 설치 하면 **bcp** 12.0 클라이언트가 설치 됩니다 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="31507-363">The **bcp** 12.0 client is installed when you install [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] tools.</span></span> <span data-ttu-id="31507-364">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]와 이전 버전의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 둘 다에 대해 도구를 설치하면 PATH 환경 변수의 값에 따라 **bcp** 12.0 클라이언트 대신 이전 **bcp** 클라이언트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-364">If tools are installed for both [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] and an earlier version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], depending on the value of the PATH environment variable, you might be using the earlier **bcp** client instead of the **bcp** 12.0 client.</span></span> <span data-ttu-id="31507-365">이 환경 변수는 실행 파일을 검색하기 위해 Windows에서 사용하는 디렉터리 집합을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-365">This environment variable defines the set of directories used by Windows to search for executable files.</span></span> <span data-ttu-id="31507-366">사용 중인 버전을 확인하려면 Windows 명령 프롬프트에서 **bcp /v** 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-366">To discover which version you are using, run the **bcp /v** command at the Windows Command Prompt.</span></span> <span data-ttu-id="31507-367">PATH 환경 변수에서 명령 경로를 설정하는 방법은 Windows 도움말을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="31507-367">For information about how to set the command path in the PATH environment variable, see Windows Help.</span></span>  
  
 <span data-ttu-id="31507-368">XML 서식 파일은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 도구를 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client와 함께 설치한 경우에만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-368">XML format files are only supported when [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tools are installed together with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 <span data-ttu-id="31507-369">**bcp** 유틸리티의 위치 또는 실행 방법과 명령 프롬프트 유틸리티 구문 표기 규칙에 대한 자세한 내용은 [명령 프롬프트 유틸리티 참조&#40;데이터베이스 엔진#41;](../tools/command-prompt-utility-reference-database-engine.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31507-369">For information about where to find or how to run the **bcp** utility and about the command prompt utilities syntax conventions, see [Command Prompt Utility Reference &#40;Database Engine&#41;](../tools/command-prompt-utility-reference-database-engine.md).</span></span>  
  
 <span data-ttu-id="31507-370">대량 가져오기 또는 내보내기 작업을 위해 데이터를 준비하는 방법은 [대량 내보내기 또는 가져오기를 위한 데이터 준비&#40;SQL Server&#41;](../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md)에 대한 지식이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-370">For information on preparing data for bulk import or export operations, see [Prepare Data for Bulk Export or Import &#40;SQL Server&#41;](../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md).</span></span>  
  
 <span data-ttu-id="31507-371">대량 가져오기로 수행된 행 삽입 작업이 트랜잭션 로그에 기록되는 경우에 대한 자세한 내용은 [대량 가져오기의 최소 로깅을 위한 선행 조건](../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31507-371">For information about when row-insert operations that are performed by bulk import are logged in the transaction log, see [Prerequisites for Minimal Logging in Bulk Import](../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md).</span></span>  
  
## <a name="native-data-file-support"></a><span data-ttu-id="31507-372">네이티브 데이터 파일 지원</span><span class="sxs-lookup"><span data-stu-id="31507-372">Native Data File Support</span></span>  
 <span data-ttu-id="31507-373">In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]에서 **bcp** 유틸리티는 [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]및 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]와 호환되는 네이티브 데이터 파일만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-373">In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], the **bcp** utility supports native data files compatible with [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)], and [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span>  
  
## <a name="computed-columns-and-timestamp-columns"></a><span data-ttu-id="31507-374">계산 열 및 타임스탬프 열</span><span class="sxs-lookup"><span data-stu-id="31507-374">Computed Columns and timestamp Columns</span></span>  
 <span data-ttu-id="31507-375">가져올 데이터 파일에 있는 계산 열 또는 `timestamp` 열의 값은 무시되며 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서 자동으로 이 값을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-375">Values in the data file being imported for computed or `timestamp` columns are ignored, and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] automatically assigns values.</span></span> <span data-ttu-id="31507-376">데이터 파일의 테이블에 계산 열 또는 `timestamp` 열의 값이 없으면 데이터를 가져올 때 서식 파일을 사용하여 테이블에 있는 계산 열 또는 `timestamp` 열을 건너뛰도록 지정합니다. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서는 해당 열에 자동으로 값을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-376">If the data file does not contain values for the computed or `timestamp` columns in the table, use a format file to specify that the computed or `timestamp` columns in the table should be skipped when importing data; [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] automatically assigns values for the column.</span></span>  
  
 <span data-ttu-id="31507-377">계산 열 및 `timestamp` 열은 보통 때와 같이 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서 데이터 파일로 대량 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-377">Computed and `timestamp` columns are bulk copied from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to a data file as usual.</span></span>  
  
## <a name="specifying-identifiers-that-contain-spaces-or-quotation-marks"></a><span data-ttu-id="31507-378">공백 또는 따옴표를 포함하는 식별자 지정</span><span class="sxs-lookup"><span data-stu-id="31507-378">Specifying Identifiers That Contain Spaces or Quotation Marks</span></span>  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="31507-379">식별자에 중간 공백이나 따옴표와 같은 문자가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-379">identifiers can include characters such as embedded spaces and quotation marks.</span></span> <span data-ttu-id="31507-380">이러한 식별자는 다음과 같이 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-380">Such identifiers must be treated as follows:</span></span>  
  
-   <span data-ttu-id="31507-381">명령 프롬프트에서 공백 또는 따옴표가 포함된 식별자나 파일 이름을 지정할 때는 식별자를 큰따옴표("")로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-381">When you specify an identifier or file name that includes a space or quotation mark at the command prompt, enclose the identifier in quotation marks ("").</span></span>  
  
     <span data-ttu-id="31507-382">예를 들어 다음 `bcp out` 명령은 `Currency Types.dat`라는 데이터 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="31507-382">For example, the following `bcp out` command creates a data file named `Currency Types.dat`:</span></span>  
  
    ```  
    bcp AdventureWorks2012.Sales.Currency out "Currency Types.dat" -T -c  
    ```  
  
-   <span data-ttu-id="31507-383">공백 또는 따옴표를 포함하는 데이터베이스 이름을 지정하려면 `-q` 옵션을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-383">To specify a database name that contains a space or quotation mark, you must use the `-q` option.</span></span>  
  
-   <span data-ttu-id="31507-384">중간 공백이나 따옴표가 포함된 소유자, 테이블 또는 뷰 이름을 지정하려면 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-384">For owner, table, or view names that contain embedded spaces or quotation marks, you can either:</span></span>  
  
    -   <span data-ttu-id="31507-385">`-q` 옵션을 지정합니다. 또는</span><span class="sxs-lookup"><span data-stu-id="31507-385">Specify the `-q` option, or</span></span>  
  
    -   <span data-ttu-id="31507-386">따옴표 안에서 소유자, 테이블 또는 뷰 이름을 대괄호([])로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-386">Enclose the owner, table, or view name in brackets ([]) inside the quotation marks.</span></span>  
  
## <a name="data-validation"></a><span data-ttu-id="31507-387">데이터 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="31507-387">Data Validation</span></span>  
 <span data-ttu-id="31507-388">**bcp** 는 이제 데이터 유효성 검사 및 데이터 검사를 강제로 실행하므로 스크립트를 데이터 파일의 잘못된 데이터에 대해 실행할 경우 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-388">**bcp** now enforces data validation and data checks that might cause scripts to fail if they are executed on invalid data in a data file.</span></span> <span data-ttu-id="31507-389">예를 들어 **bcp** 는 이제 다음을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-389">For example, **bcp** now verifies that:</span></span>  
  
-   <span data-ttu-id="31507-390">`float` 또는 `real` 데이터 형식의 네이티브 표시가 유효한지 여부</span><span class="sxs-lookup"><span data-stu-id="31507-390">The native representation of `float` or `real` data types are valid.</span></span>  
  
-   <span data-ttu-id="31507-391">유니코드 데이터의 길이가 짝수 바이트인지 여부</span><span class="sxs-lookup"><span data-stu-id="31507-391">Unicode data has an even-byte length.</span></span>  
  
 <span data-ttu-id="31507-392">이전 버전의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서 대량으로 가져올 수 있었던 잘못된 데이터 형식은 이제 로드되지 않습니다. 이전 버전에서는 클라이언트가 잘못된 데이터에 액세스해야 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-392">Forms of invalid data that could be bulk imported in earlier versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] might fail to load now; whereas, in earlier versions, the failure did not occur until a client tried to access the invalid data.</span></span> <span data-ttu-id="31507-393">추가 유효성 검사를 수행하면 대량 로드 이후 데이터를 쿼리할 때 발생할 수 있는 예상치 못한 문제가 최소화됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-393">The added validation minimizes surprises when querying the data after bulk load.</span></span>  
  
## <a name="bulk-exporting-or-importing-sqlxml-documents"></a><span data-ttu-id="31507-394">SQLXML 문서 대량 내보내기 또는 가져오기</span><span class="sxs-lookup"><span data-stu-id="31507-394">Bulk Exporting or Importing SQLXML Documents</span></span>  
 <span data-ttu-id="31507-395">SQLXML 데이터를 대량으로 내보내거나 가져오려면 서식 파일에서 다음 데이터 형식 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-395">To bulk export or import SQLXML data, use one of the following data types in your format file.</span></span>  
  
|<span data-ttu-id="31507-396">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="31507-396">Data type</span></span>|<span data-ttu-id="31507-397">영향</span><span class="sxs-lookup"><span data-stu-id="31507-397">Effect</span></span>|  
|---------------|------------|  
|<span data-ttu-id="31507-398">SQLCHAR 또는 SQLVARYCHAR</span><span class="sxs-lookup"><span data-stu-id="31507-398">SQLCHAR or SQLVARYCHAR</span></span>|<span data-ttu-id="31507-399">데이터를 클라이언트 코드 페이지나 데이터 정렬에 포함된 코드 페이지로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="31507-399">The data is sent in the client code page or in the code page implied by the collation).</span></span> <span data-ttu-id="31507-400">이는 서식 파일을 지정하지 않고 `-c` 스위치를 지정하는 것과 효과가 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-400">The effect is the same as specifying the `-c` switch without specifying a format file.</span></span>|  
|<span data-ttu-id="31507-401">SQLNCHAR 또는 SQLNVARCHAR</span><span class="sxs-lookup"><span data-stu-id="31507-401">SQLNCHAR or SQLNVARCHAR</span></span>|<span data-ttu-id="31507-402">데이터를 유니코드로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="31507-402">The data is sent as Unicode.</span></span> <span data-ttu-id="31507-403">이는 서식 파일을 지정하지 않고 `-w` 스위치를 지정하는 것과 효과가 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-403">The effect is the same as specifying the `-w` switch without specifying a format file.</span></span>|  
|<span data-ttu-id="31507-404">SQLBINARY 또는 SQLVARYBIN</span><span class="sxs-lookup"><span data-stu-id="31507-404">SQLBINARY or SQLVARYBIN</span></span>|<span data-ttu-id="31507-405">데이터를 변환하지 않고 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="31507-405">The data is sent without any conversion.</span></span>|  
  
## <a name="permissions"></a><span data-ttu-id="31507-406">사용 권한</span><span class="sxs-lookup"><span data-stu-id="31507-406">Permissions</span></span>  
 <span data-ttu-id="31507-407">**bcpout** 작업을 수행하려면 원본 테이블에 대한 SELECT 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-407">A **bcpout** operation requires SELECT permission on the source table.</span></span>  
  
 <span data-ttu-id="31507-408">**bcpin** 작업을 수행하려면 적어도 대상 테이블에 대한 SELECT/INSERT 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-408">A **bcpin** operation minimally requires SELECT/INSERT permissions on the target table.</span></span> <span data-ttu-id="31507-409">또한 다음과 같은 경우 ALTER TABLE 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-409">In addition, ALTER TABLE permission is required if any of the following is true:</span></span>  
  
-   <span data-ttu-id="31507-410">제약 조건이 있으며 CHECK_CONSTRAINTS 힌트가 지정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-410">Constraints exist and the CHECK_CONSTRAINTS hint is not specified.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="31507-411">기본적으로 제약 조건은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-411">Disabling constraints is the default behavior.</span></span> <span data-ttu-id="31507-412">제약 조건을 명시적으로 사용하려면 CHECK_CONSTRAINTS 힌트와 함께 **-h** 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-412">To enable constraints explicitly, use the **-h** option with the CHECK_CONSTRAINTS hint.</span></span>  
  
-   <span data-ttu-id="31507-413">트리거가 있으며 FIRE_TRIGGER 힌트가 지정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-413">Triggers exist and the FIRE_TRIGGER hint is not specified.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="31507-414">기본적으로 트리거는 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-414">By default, triggers are not fired.</span></span> <span data-ttu-id="31507-415">트리거를 명시적으로 실행하려면 FIRE_TRIGGERS 힌트와 함께 **-h** 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-415">To fire triggers explicitly, use the **-h** option with the FIRE_TRIGGERS hint.</span></span>  
  
-   <span data-ttu-id="31507-416">**-E** 옵션을 사용하여 데이터 파일에서 ID 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="31507-416">You use the **-E** option to import identity values from a data file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="31507-417">대상 테이블에 대해 ALTER TABLE 권한이 필요하게 된 것은 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]부터였습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-417">Requiring ALTER TABLE permission on the target table was new in [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="31507-418">이 요구 사항으로 인해 사용자 계정에 대상 테이블에 대한 ALTER 테이블 권한이 없을 경우 트리거 및 제약 조건 검사를 실행하지 않는 **bcp** 스크립트가 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-418">This new requirement might cause **bcp** scripts that do not enforce triggers and constraint checks to fail if the user account lacks ALTER table permissions for the target table.</span></span>  
  
## <a name="character-mode--c-and-native-mode--n-best-practices"></a><span data-ttu-id="31507-419">문자 모드(-c) 및 기본 모드(-n) 최선의 구현 방법</span><span class="sxs-lookup"><span data-stu-id="31507-419">Character Mode (-c) and Native Mode (-n) Best Practices</span></span>  
 <span data-ttu-id="31507-420">이 섹션에는 문자 모드(-c) 및 기본 모드(-n) 사용 시의 권장 사항이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-420">This section has recommendations for to character mode (-c) and native mode (-n).</span></span>  
  
-   <span data-ttu-id="31507-421">(관리자/사용자) 가능하면 구분 기호 문제를 방지하기 위해 기본 모드(-n)를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="31507-421">(Administrator/User) When possible, use native format (-n) to avoid the separator issue.</span></span> <span data-ttu-id="31507-422">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]를 사용하여 내보내기 및 가져오기를 수행하려면 기본 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-422">Use the native format to export and import using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="31507-423">데이터를 비 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스로 가져오려는 경우에는 -c 또는 -w 옵션을 사용하여[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서 데이터를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="31507-423">Export data from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] using the -c or -w option if the data will be imported to a non-[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span>  
  
-   <span data-ttu-id="31507-424">(관리자) BCP OUT를 사용할 때는 데이터를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-424">(Administrator) Verify data when using BCP OUT.</span></span> <span data-ttu-id="31507-425">예를 들어 BCP OUT, BCP IN, BCP OUT을 차례로 사용하는 경우에는 데이터가 정상적으로 내보내기되었으며 몇몇 데이터 값의 일부분으로 종결자 값이 사용되지 않았는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-425">For example, when you use BCP OUT, BCP IN, and then BCP OUT verify that the data is properly exported and the terminator values are not used as part of some data value.</span></span> <span data-ttu-id="31507-426">종결자 값과 데이터 값 간의 충돌을 방지하려면 임의의 16진수 값을 사용하여 기본 종결자를 무시할 수 있습니다(-t 및 -r 옵션 사용).</span><span class="sxs-lookup"><span data-stu-id="31507-426">Please consider overriding the default terminators (using -t and -r options) with random hexadecimal values to avoid conflicts between terminator values and data values.</span></span>  
  
-   <span data-ttu-id="31507-427">(사용자) 실제 문자열 값 간의 충돌 가능성을 최소화하려면 길고 고유한 종결자(바이트 또는 문자 시퀀스)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-427">(User) Use a long and unique terminator (any sequence of bytes or characters) to minimize the possibility of a conflict with the actual string value.</span></span> <span data-ttu-id="31507-428">이렇게 하려면 -t 및 -r 옵션을 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31507-428">This can be done by using the -t and -r options.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="31507-429">예</span><span class="sxs-lookup"><span data-stu-id="31507-429">Examples</span></span>  
 <span data-ttu-id="31507-430">이 섹션에는 다음 예제가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-430">This section contains the following examples:</span></span>  
  
-   <span data-ttu-id="31507-431">A.</span><span class="sxs-lookup"><span data-stu-id="31507-431">A.</span></span> <span data-ttu-id="31507-432">데이터 파일로 테이블 행 복사(트러스트된 연결 사용)</span><span class="sxs-lookup"><span data-stu-id="31507-432">Copying table rows into a data file (with a trusted connection)</span></span>  
  
-   <span data-ttu-id="31507-433">B.</span><span class="sxs-lookup"><span data-stu-id="31507-433">B.</span></span> <span data-ttu-id="31507-434">데이터 파일로 테이블 행 복사(혼합 모드 인증 사용)</span><span class="sxs-lookup"><span data-stu-id="31507-434">Copying table rows into a data file (with Mixed-mode Authentication)</span></span>  
  
-   <span data-ttu-id="31507-435">C.</span><span class="sxs-lookup"><span data-stu-id="31507-435">C.</span></span> <span data-ttu-id="31507-436">파일에서 테이블로 데이터 복사</span><span class="sxs-lookup"><span data-stu-id="31507-436">Copying data from a file to a table</span></span>  
  
-   <span data-ttu-id="31507-437">D.</span><span class="sxs-lookup"><span data-stu-id="31507-437">D.</span></span> <span data-ttu-id="31507-438">데이터 파일로 특정 열 복사</span><span class="sxs-lookup"><span data-stu-id="31507-438">Copying a specific column into a data file</span></span>  
  
-   <span data-ttu-id="31507-439">E.</span><span class="sxs-lookup"><span data-stu-id="31507-439">E.</span></span> <span data-ttu-id="31507-440">데이터 파일로 특정 행 복사</span><span class="sxs-lookup"><span data-stu-id="31507-440">Copying a specific row into a data file</span></span>  
  
-   <span data-ttu-id="31507-441">F.</span><span class="sxs-lookup"><span data-stu-id="31507-441">F.</span></span> <span data-ttu-id="31507-442">쿼리에서 데이터 파일로 데이터 복사</span><span class="sxs-lookup"><span data-stu-id="31507-442">Copying data from a query to a data file</span></span>  
  
-   <span data-ttu-id="31507-443">G.</span><span class="sxs-lookup"><span data-stu-id="31507-443">G.</span></span> <span data-ttu-id="31507-444">비 XML 서식 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="31507-444">Creating a non-XML format file</span></span>  
  
-   <span data-ttu-id="31507-445">H.</span><span class="sxs-lookup"><span data-stu-id="31507-445">H.</span></span> <span data-ttu-id="31507-446">XML 서식 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="31507-446">Creating an XML format file</span></span>  
  
-   <span data-ttu-id="31507-447">9\.</span><span class="sxs-lookup"><span data-stu-id="31507-447">I.</span></span> <span data-ttu-id="31507-448">**bcp**에서 서식 파일을 사용하여 대량 가져오기 수행</span><span class="sxs-lookup"><span data-stu-id="31507-448">Using a format file to bulk import with **bcp**</span></span>  
  
### <a name="a-copying-table-rows-into-a-data-file-with-a-trusted-connection"></a><span data-ttu-id="31507-449">A.</span><span class="sxs-lookup"><span data-stu-id="31507-449">A.</span></span> <span data-ttu-id="31507-450">데이터 파일로 테이블 행 복사(트러스트된 연결 사용)</span><span class="sxs-lookup"><span data-stu-id="31507-450">Copying table rows into a data file (with a trusted connection)</span></span>  
 <span data-ttu-id="31507-451">다음 예에서는 **테이블의** out `AdventureWorks2012.Sales.Currency` 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-451">The following example illustrates the **out** option on the `AdventureWorks2012.Sales.Currency` table.</span></span> <span data-ttu-id="31507-452">이 예에서는 `Currency.dat`라는 데이터 파일을 만들고 문자 형식을 사용하여 테이블 데이터를 파일에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-452">This example creates a data file named `Currency.dat` and copies the table data into it using character format.</span></span> <span data-ttu-id="31507-453">이 예에서는 Windows 인증을 사용하고 있고 **bcp** 명령을 실행 중인 서버 인스턴스에 트러스트된 연결이 설정되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-453">The example assumes that you are using Windows Authentication and have a trusted connection to the server instance on which you are running the **bcp** command.</span></span>  
  
 <span data-ttu-id="31507-454">명령 프롬프트에서 다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-454">At a command prompt, enter the following command:</span></span>  
  
```  
bcp AdventureWorks2012.Sales.Currency out Currency.dat -T -c  
```  
  
### <a name="b-copying-table-rows-into-a-data-file-with-mixed-mode-authentication"></a><span data-ttu-id="31507-455">B.</span><span class="sxs-lookup"><span data-stu-id="31507-455">B.</span></span> <span data-ttu-id="31507-456">데이터 파일로 테이블 행 복사(혼합 모드 인증 사용)</span><span class="sxs-lookup"><span data-stu-id="31507-456">Copying table rows into a data file (with mixed-mode authentication)</span></span>  
 <span data-ttu-id="31507-457">다음 예에서는 **테이블의** out `AdventureWorks2012.Sales.Currency` 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-457">The following example illustrates the **out** option on the `AdventureWorks2012.Sales.Currency` table.</span></span> <span data-ttu-id="31507-458">이 예에서는 `Currency.dat`라는 데이터 파일을 만들고 문자 형식을 사용하여 테이블 데이터를 파일에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-458">This example creates a data file named `Currency.dat` and copies the table data into it using character format.</span></span>  
  
 <span data-ttu-id="31507-459">이 예에서는 혼합 모드 인증을 사용하고 있다고 가정합니다. **-U** 스위치를 사용하여 로그인 ID를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-459">The example assumes that you are using mixed-mode authentication, you must use the **-U** switch to specify your login ID.</span></span> <span data-ttu-id="31507-460">또한 로컬 컴퓨터에 있는 기본 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 연결하지 않는 한 **-S** 스위치를 사용하여 시스템 이름을 지정하고 원하는 경우 인스턴스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-460">Also, unless you are connecting to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the local computer, use the **-S** switch to specify the system name and, optionally, an instance name.</span></span>  
  
```  
bcp AdventureWorks2012.Sales.Currency out Currency.dat -c -U<login_id> -S<server_name\instance_name>  
```  
  
 <span data-ttu-id="31507-461">시스템에서 암호를 묻는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-461">The system will prompt you for your password.</span></span>  
  
### <a name="c-copying-data-from-a-file-to-a-table"></a><span data-ttu-id="31507-462">C.</span><span class="sxs-lookup"><span data-stu-id="31507-462">C.</span></span> <span data-ttu-id="31507-463">파일에서 테이블로 데이터 복사</span><span class="sxs-lookup"><span data-stu-id="31507-463">Copying data from a file to a table</span></span>  
 <span data-ttu-id="31507-464">다음 예에서는 앞의 예에서 만든 `Currency.dat` 파일을 사용하여 **in** 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-464">The following example illustrates the **in** option by using the file created in the preceding example (`Currency.dat`).</span></span> <span data-ttu-id="31507-465">그러나 먼저 이 예에서는 데이터를 복사해 넣을 빈 `AdventureWorks2012 Sales.Currency` 테이블 복사본 `Sales.Currency2`를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="31507-465">First, however, this example creates an empty copy of the `AdventureWorks2012 Sales.Currency` table, `Sales.Currency2`, into which the data is copied.</span></span> <span data-ttu-id="31507-466">이 예에서는 Windows 인증을 사용하고 있고 **bcp** 명령을 실행 중인 서버 인스턴스에 트러스트된 연결이 설정되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-466">The example assumes that you are using Windows Authentication and have a trusted connection to the server instance on which you are running the **bcp** command.</span></span>  
  
 <span data-ttu-id="31507-467">빈 테이블을 만들려면 쿼리 편집기에서 다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-467">To create the empty table, in Query Editor, enter the following command:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * INTO AdventureWorks2012.Sales.Currency2   
FROM AdventureWorks2012.Sales.Currency WHERE 1=2;  
```  
  
 <span data-ttu-id="31507-468">문자 데이터를 새 테이블로 대량 복사하려면 즉, 데이터를 가져오려면 명령 프롬프트에서 다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-468">To bulk copy the character data into the new table, that is to import the data, enter the following command at a command prompt:</span></span>  
  
```  
bcp AdventureWorks2012.Sales.Currency2 in Currency.dat -T -c  
```  
  
 <span data-ttu-id="31507-469">명령이 성공적으로 실행되었는지 확인하려면 쿼리 편집기에서 테이블 내용을 표시하고 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-469">To verify that the command succeeded, display the contents of the table in Query Editor, and enter:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * FROM Sales.Currency2  
```  
  
### <a name="d-copying-a-specific-column-into-a-data-file"></a><span data-ttu-id="31507-470">D.</span><span class="sxs-lookup"><span data-stu-id="31507-470">D.</span></span> <span data-ttu-id="31507-471">데이터 파일로 특정 열 복사</span><span class="sxs-lookup"><span data-stu-id="31507-471">Copying a specific column into a data file</span></span>  
 <span data-ttu-id="31507-472">특정 열을 복사하려면 **queryout** 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-472">To copy a specific column, you can use the **queryout** option.</span></span> <span data-ttu-id="31507-473">다음 예에서는 `Name` 테이블의 `Sales.Currency` 열만 데이터 파일로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-473">The following example copies only the `Name` column of the `Sales.Currency` table into a data file.</span></span> <span data-ttu-id="31507-474">이 예에서는 Windows 인증을 사용하고 있고 **bcp** 명령을 실행 중인 서버 인스턴스에 트러스트된 연결이 설정되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-474">The example assumes that you are using Windows Authentication and have a trusted connection to the server instance on which you are running the **bcp** command.</span></span>  
  
 <span data-ttu-id="31507-475">Windows 명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-475">At the Windows command prompt, enter:</span></span>  
  
```  
bcp "SELECT Name FROM AdventureWorks.Sales.Currency" queryout Currency.Name.dat -T -c  
```  
  
### <a name="e-copying-a-specific-row-into-a-data-file"></a><span data-ttu-id="31507-476">E.</span><span class="sxs-lookup"><span data-stu-id="31507-476">E.</span></span> <span data-ttu-id="31507-477">데이터 파일로 특정 행 복사</span><span class="sxs-lookup"><span data-stu-id="31507-477">Copying a specific row into a data file</span></span>  
 <span data-ttu-id="31507-478">특정 행을 복사하려면 **queryout** 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-478">To copy a specific row, you can use the **queryout** option.</span></span> <span data-ttu-id="31507-479">다음 예에서는 `Jarrod Rana`라는 연락처 행만 `AdventureWorks2012.Person.Person` 테이블에서 데이터 파일(`Jarrod Rana.dat`)로 복사합니다. 이 예에서는 Windows 인증을 사용하고 있고 **bcp** 명령을 실행 중인 서버 인스턴스에 트러스트된 연결이 설정되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-479">The following example copies only the row for the contact named `Jarrod Rana` from the `AdventureWorks2012.Person.Person` table into a data file (`Jarrod Rana.dat`).The example assumes that you are using Windows Authentication and have a trusted connection to the server instance on which you are running the **bcp** command.</span></span>  
  
 <span data-ttu-id="31507-480">Windows 명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-480">At the Windows command prompt, enter:</span></span>  
  
```  
bcp "SELECT * FROM AdventureWorks2012.Person.Person WHERE FirstName='Jarrod' AND LastName='Rana' "  queryout "Jarrod Rana.dat" -T -c  
```  
  
### <a name="f-copying-data-from-a-query-to-a-data-file"></a><span data-ttu-id="31507-481">F.</span><span class="sxs-lookup"><span data-stu-id="31507-481">F.</span></span> <span data-ttu-id="31507-482">쿼리에서 데이터 파일로 데이터 복사</span><span class="sxs-lookup"><span data-stu-id="31507-482">Copying data from a query to a data file</span></span>  
 <span data-ttu-id="31507-483">[!INCLUDE[tsql](../includes/tsql-md.md)] 문의 결과 집합을 데이터 파일로 복사하려면 **queryout** 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-483">To copy the result set from a [!INCLUDE[tsql](../includes/tsql-md.md)] statement to a data file, use the **queryout** option.</span></span> <span data-ttu-id="31507-484">다음 예에서는 `AdventureWorks2012.Person.Person` 테이블에서 성과 이름을 기준으로 정렬된 이름을 `Contacts.txt` 데이터 파일로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-484">The following example copies the names from the `AdventureWorks2012.Person.Person` table, ordered by last name then first name, into the `Contacts.txt` data file.</span></span> <span data-ttu-id="31507-485">이 예에서는 Windows 인증을 사용하고 있고 **bcp** 명령을 실행 중인 서버 인스턴스에 트러스트된 연결이 설정되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-485">The example assumes that you are using Windows Authentication and have a trusted connection to the server instance on which you are running the **bcp** command.</span></span>  
  
 <span data-ttu-id="31507-486">Windows 명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-486">At the Windows command prompt, enter:</span></span>  
  
```  
bcp "SELECT FirstName, LastName FROM AdventureWorks2012.Person.Person ORDER BY LastName, Firstname" queryout Contacts.txt -c -T  
```  
  
### <a name="g-creating-a-non-xml-format-file"></a><span data-ttu-id="31507-487">G.</span><span class="sxs-lookup"><span data-stu-id="31507-487">G.</span></span> <span data-ttu-id="31507-488">비 XML 서식 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="31507-488">Creating a non-XML format file</span></span>  
 <span data-ttu-id="31507-489">다음 예에서는 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 데이터베이스의 `Currency.fmt` 테이블에 대해 `Sales.Currency`라는 비 XML 서식 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="31507-489">The following example creates a non-XML format file, `Currency.fmt`, for the `Sales.Currency` table in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="31507-490">이 예에서는 Windows 인증을 사용하고 있고 **bcp** 명령을 실행 중인 서버 인스턴스에 트러스트된 연결이 설정되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-490">The example assumes that you are using Windows Authentication and have a trusted connection to the server instance on which you are running the **bcp** command.</span></span>  
  
 <span data-ttu-id="31507-491">Windows 명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-491">At the Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks2012.Sales.Currency format nul -T -c  -f Currency.fmt  
```  
  
 <span data-ttu-id="31507-492">자세한 내용은 [비 XML 서식 파일&#40;SQL Server&#41;](../relational-databases/import-export/xml-format-files-sql-server.md)에서 원래 지원했던 서식 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="31507-492">For more information, see [Non-XML Format Files &#40;SQL Server&#41;](../relational-databases/import-export/xml-format-files-sql-server.md).</span></span>  
  
### <a name="h-creating-an-xml-format-file"></a><span data-ttu-id="31507-493">H.</span><span class="sxs-lookup"><span data-stu-id="31507-493">H.</span></span> <span data-ttu-id="31507-494">XML 서식 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="31507-494">Creating an XML format file</span></span>  
 <span data-ttu-id="31507-495">다음 예에서는 `Currency.xml` 데이터베이스의 `Sales.Currency` 테이블에 대해 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 이라는 XML 서식 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="31507-495">The following example creates an XML format file named `Currency.xml` for the `Sales.Currency` table in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="31507-496">이 예에서는 Windows 인증을 사용하고 있고 **bcp** 명령을 실행 중인 서버 인스턴스에 트러스트된 연결이 설정되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-496">The example assumes that you are using Windows Authentication and have a trusted connection to the server instance on which you are running the **bcp** command.</span></span>  
  
 <span data-ttu-id="31507-497">Windows 명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-497">At the Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks2012.Sales.Currency format nul -T -c -x -f Currency.xml  
```  
  
> [!NOTE]  
>  <span data-ttu-id="31507-498">**-x** 스위치를 사용하려면 **bcp** 9.0 클라이언트를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-498">To use the **-x** switch, you must be using a **bcp** 9.0 client.</span></span> <span data-ttu-id="31507-499">**Bcp** 9.0 클라이언트를 사용 하는 방법에 대 한 자세한 내용은 "주의"를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="31507-499">For information about how to use the **bcp** 9.0 client, see "Remarks."</span></span>  
  
 <span data-ttu-id="31507-500">자세한 내용은 [XML 서식 파일&#40;SQL Server&#41;](../relational-databases/import-export/xml-format-files-sql-server.md)의 두 가지 서식 파일 유형을 대량으로 내보내고 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-500">For more information, see [XML Format Files &#40;SQL Server&#41;](../relational-databases/import-export/xml-format-files-sql-server.md).</span></span>  
  
### <a name="i-using-a-format-file-to-bulk-import-with-bcp"></a><span data-ttu-id="31507-501">9\.</span><span class="sxs-lookup"><span data-stu-id="31507-501">I.</span></span> <span data-ttu-id="31507-502">bcp에서 서식 파일을 사용하여 대량 가져오기 수행</span><span class="sxs-lookup"><span data-stu-id="31507-502">Using a format file to bulk import with bcp</span></span>  
 <span data-ttu-id="31507-503">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스로 데이터를 가져올 때 이전에 만든 서식 파일을 사용하려면 **in** 옵션과 함께 **-f** 스위치를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-503">To use a previously created format file when importing data into an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], use the **-f** switch with the **in** option.</span></span> <span data-ttu-id="31507-504">예를 들어 다음 명령은 이전에 만든 서식 파일인 `Currency.dat`을 사용하여 데이터 파일 `Sales.Currency`의 내용을 `Sales.Currency2` 테이블의 복사본인 `Currency.xml`로 대량 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-504">For example, the following command bulk copies the contents of a data file, `Currency.dat`, into a copy of the `Sales.Currency` table (`Sales.Currency2`) by using the previously created format file (`Currency.xml`).</span></span> <span data-ttu-id="31507-505">이 예에서는 Windows 인증을 사용하고 있고 **bcp** 명령을 실행 중인 서버 인스턴스에 트러스트된 연결이 설정되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-505">The example assumes that you are using Windows Authentication and have a trusted connection to the server instance on which you are running the **bcp** command.</span></span>  
  
 <span data-ttu-id="31507-506">Windows 명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-506">At the Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks2012.Sales.Currency2 in Currency.dat -T -f Currency.xml  
```  
  
> [!NOTE]  
>  <span data-ttu-id="31507-507">데이터 파일 필드와 테이블 열의 숫자, 순서, 데이터 형식 등이 다른 경우 서식 파일을 사용하면 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="31507-507">Format files are useful when the data file fields are different from the table columns; for example, in their number, ordering, or data types.</span></span> <span data-ttu-id="31507-508">자세한 내용은 [데이터를 가져오거나 내보내기 위한 서식 파일&#40;SQL Server&#41;](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31507-508">For more information, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="31507-509">추가 예</span><span class="sxs-lookup"><span data-stu-id="31507-509">Additional Examples</span></span>  
 <span data-ttu-id="31507-510">다음 항목에는 **bcp**를 사용 하는 예가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31507-510">The following topics contain examples of using **bcp**:</span></span>  
  
-   [<span data-ttu-id="31507-511">서식 파일 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="31507-511">Create a Format File &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="31507-512">XML 문서 대량 가져오기 및 내보내기 예제&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="31507-512">Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [<span data-ttu-id="31507-513">데이터 대량 가져오기 중 ID 값 유지&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="31507-513">Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [<span data-ttu-id="31507-514">대량 가져오기 수행 중 Null 유지 또는 기본값 사용&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="31507-514">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [<span data-ttu-id="31507-515">필드 및 행 종결자 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="31507-515">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)  
  
-   [<span data-ttu-id="31507-516">서식 파일을 사용하여 데이터 대량 가져오기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="31507-516">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="31507-517">문자 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="31507-517">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="31507-518">네이티브 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="31507-518">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="31507-519">유니코드 문자 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="31507-519">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="31507-520">유니코드 네이티브 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="31507-520">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="31507-521">참고 항목</span><span class="sxs-lookup"><span data-stu-id="31507-521">See Also</span></span>  
 <span data-ttu-id="31507-522">[대량 내보내기 또는 가져오기를 위한 데이터 준비 &#40;SQL Server&#41;](../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="31507-522">[Prepare Data for Bulk Export or Import &#40;SQL Server&#41;](../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md) </span></span>  
 <span data-ttu-id="31507-523">[BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="31507-523">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="31507-524">[OPENROWSET&#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="31507-524">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="31507-525">[Transact-sql&#41;&#40;QUOTED_IDENTIFIER 설정](/sql/t-sql/statements/set-quoted-identifier-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="31507-525">[SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql) </span></span>  
 <span data-ttu-id="31507-526">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="31507-526">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="31507-527">[Transact-sql&#41;sp_tableoption &#40;](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="31507-527">[sp_tableoption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql) </span></span>  
 [<span data-ttu-id="31507-528">데이터를 가져오거나 내보내기 위한 서식 파일&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="31507-528">Format Files for Importing or Exporting Data &#40;SQL Server&#41;</span></span>](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)  
  
  

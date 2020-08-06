---
title: tablediff 유틸리티 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- comparing data
- tablediff utility
- tables [SQL Server replication]
- table comparisons [SQL Server]
- command prompt utilities [SQL Server], tablediff
- troubleshooting [SQL Server replication], non-convergence
- non-convergence [SQL Server]
ms.assetid: 3c3cb865-7a4d-4d66-98f2-5935e28929fc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0a23465a7d2c7db53475a6dca81a8471a3b78b50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735708"
---
# <a name="tablediff-utility"></a><span data-ttu-id="f69e7-102">tablediff 유틸리티</span><span class="sxs-lookup"><span data-stu-id="f69e7-102">tablediff Utility</span></span>
  <span data-ttu-id="f69e7-103">**tablediff** 유틸리티는 두 테이블에 포함된 데이터의 불일치 여부를 비교하는 데 사용되며, 복제 토폴로지의 데이터 불일치 문제를 해결하는 데 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-103">The **tablediff** utility is used to compare the data in two tables for non-convergence, and is particularly useful for troubleshooting non-convergence in a replication topology.</span></span> <span data-ttu-id="f69e7-104">명령 프롬프트나 배치 파일에서 이 유틸리티를 사용하여 다음 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-104">This utility can be used from the command prompt or in a batch file to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="f69e7-105">복제 게시자 역할을 하는 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 있는 원본 테이블과 복제 구독자 역할을 하는 하나 이상의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 있는 대상 테이블을 행 단위로 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-105">A row by row comparison between a source table in an instance of [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] acting as a replication Publisher and the destination table at one or more instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] acting as replication Subscribers.</span></span>  
  
-   <span data-ttu-id="f69e7-106">행 개수와 스키마만 비교하여 비교 작업을 빨리 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-106">Perform a fast comparison by only comparing row counts and schema.</span></span>  
  
-   <span data-ttu-id="f69e7-107">열 수준에서 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-107">Perform column-level comparisons.</span></span>  
  
-   <span data-ttu-id="f69e7-108">대상 서버의 불일치를 해결하는 [!INCLUDE[tsql](../includes/tsql-md.md)] 스크립트를 생성하여 원본 테이블과 대상 테이블을 일치시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-108">Generate a [!INCLUDE[tsql](../includes/tsql-md.md)] script to fix discrepancies at the destination server to bring the source and destination tables into convergence.</span></span>  
  
-   <span data-ttu-id="f69e7-109">결과를 출력 파일이나 대상 데이터베이스의 테이블에 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-109">Log results to an output file or into a table in the destination database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f69e7-110">구문</span><span class="sxs-lookup"><span data-stu-id="f69e7-110">Syntax</span></span>  
  
```  
  
      tablediff   
[ -? ] |   
{  
        -sourceserversource_server_name[\instance_name]  
        -sourcedatabasesource_database-sourcetablesource_table_name   
    [ -sourceschemasource_schema_name ]  
    [ -sourcepasswordsource_password ]  
    [ -sourceusersource_login ]  
    [ -sourcelocked ]  
        -destinationserverdestination_server_name[\instance_name]  
        -destinationdatabasesubscription_database-destinationtabledestination_table   
    [ -destinationschemadestination_schema_name ]  
    [ -destinationpassworddestination_password ]  
    [ -destinationuserdestination_login ]  
    [ -destinationlocked ]  
    [ -blarge_object_bytes ]   
    [ -bfnumber_of_statements ]   
    [ -c ]   
    [ -dt ]   
    [ -ettable_name ]   
    [ -f [ file_name ] ]   
    [ -ooutput_file_name ]   
    [ -q ]   
    [ -rcnumber_of_retries ]   
    [ -riretry_interval ]   
    [ -strict ]  
    [ -tconnection_timeouts ]   
}  
```  
  
## <a name="arguments"></a><span data-ttu-id="f69e7-111">인수</span><span class="sxs-lookup"><span data-stu-id="f69e7-111">Arguments</span></span>  
 <span data-ttu-id="f69e7-112">[ **-?**</span><span class="sxs-lookup"><span data-stu-id="f69e7-112">[ **-?**</span></span> <span data-ttu-id="f69e7-113">]</span><span class="sxs-lookup"><span data-stu-id="f69e7-113">]</span></span>  
 <span data-ttu-id="f69e7-114">지원되는 매개 변수 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-114">Returns the list of supported parameters.</span></span>  
  
 <span data-ttu-id="f69e7-115">**-sourceerver** *source_server_name*[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="f69e7-115">**-sourceserver** *source_server_name*[**\\**_instance_name_]</span></span>  
 <span data-ttu-id="f69e7-116">원본 서버의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-116">Is the name of the source server.</span></span> <span data-ttu-id="f69e7-117">의 기본 인스턴스에 대 한 _원본 \_ 서버 \_ 이름을_ 지정 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-117">Specify _source\_server\_name_ for the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f69e7-118">의 명명 된 인스턴스에 대 한 _원본 \_ 서버 \_ 이름_ **\\** _인스턴스 \_ 이름을_ 지정 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-118">Specify _source\_server\_name_**\\**_instance\_name_ for a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="f69e7-119">**-sourcedatabase** *source_database*</span><span class="sxs-lookup"><span data-stu-id="f69e7-119">**-sourcedatabase** *source_database*</span></span>  
 <span data-ttu-id="f69e7-120">원본 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-120">Is the name of the source database.</span></span>  
  
 <span data-ttu-id="f69e7-121">**-sourcetable** *source_table_name*</span><span class="sxs-lookup"><span data-stu-id="f69e7-121">**-sourcetable** *source_table_name*</span></span>  
 <span data-ttu-id="f69e7-122">검사할 원본 테이블의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-122">Is the name of the source table being checked.</span></span>  
  
 <span data-ttu-id="f69e7-123">**-sourceschema** *source_schema_name*</span><span class="sxs-lookup"><span data-stu-id="f69e7-123">**-sourceschema** *source_schema_name*</span></span>  
 <span data-ttu-id="f69e7-124">원본 테이블의 스키마 소유자입니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-124">The schema owner of the source table.</span></span> <span data-ttu-id="f69e7-125">기본적으로 테이블 소유자를 dbo로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-125">By default, the table owner is assumed to be dbo.</span></span>  
  
 <span data-ttu-id="f69e7-126">**-sourcepassword** *source_password*</span><span class="sxs-lookup"><span data-stu-id="f69e7-126">**-sourcepassword** *source_password*</span></span>  
 <span data-ttu-id="f69e7-127">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 사용하여 원본 서버에 연결하는 데 사용되는 로그인 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-127">Is the password for the login used to connect to the source server using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f69e7-128">가능하면 런타임 동안 보안 자격 증명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-128">When possible, supply security credentials at runtime.</span></span> <span data-ttu-id="f69e7-129">스크립트 파일에 자격 증명을 저장해야 하는 경우에는 무단으로 액세스하지 못하도록 파일에 보안을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-129">If you must store credentials in a script file, you should secure the file to prevent unauthorized access.</span></span>  
  
 <span data-ttu-id="f69e7-130">**-sourceuser** *source_login*</span><span class="sxs-lookup"><span data-stu-id="f69e7-130">**-sourceuser** *source_login*</span></span>  
 <span data-ttu-id="f69e7-131">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 사용하여 원본 서버에 연결하는 데 사용되는 로그인입니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-131">Is the login used to connect to the source server using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="f69e7-132">*source_login* 을 지정하지 않으면 원본 서버에 연결할 때 Windows 인증이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-132">If *source_login* is not supplied, then Windows Authentication is used when connecting to the source server.</span></span> [!INCLUDE[ssNoteWinAuthentication](../includes/ssnotewinauthentication-md.md)]  
  
 <span data-ttu-id="f69e7-133">**-sourcelocked**</span><span class="sxs-lookup"><span data-stu-id="f69e7-133">**-sourcelocked**</span></span>  
 <span data-ttu-id="f69e7-134">비교를 수행하는 동안 TABLOCK 및 HOLDLOCK 테이블 힌트를 사용하여 원본 테이블이 잠깁니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-134">The source table is locked during the comparison using the TABLOCK and HOLDLOCK table hints.</span></span>  
  
 <span data-ttu-id="f69e7-135">**-destinationserver** *destination_server_name*[ **\\** _instance \_ name_]</span><span class="sxs-lookup"><span data-stu-id="f69e7-135">**-destinationserver** *destination_server_name*[**\\**_instance\_name_]</span></span>  
 <span data-ttu-id="f69e7-136">대상 서버의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-136">Is the name of the destination server.</span></span> <span data-ttu-id="f69e7-137">*의 기본 인스턴스에 대해* destination_server_name [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-137">Specify *destination_server_name* for the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f69e7-138">의 명명 된 인스턴스에 대 한 _대상 \_ 서버 \_ 이름_ **\\** _인스턴스 \_ 이름을_ 지정 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-138">Specify _destination\_server\_name_**\\**_instance\_name_ for a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="f69e7-139">**-destinationdatabase** *subscription_database*</span><span class="sxs-lookup"><span data-stu-id="f69e7-139">**-destinationdatabase** *subscription_database*</span></span>  
 <span data-ttu-id="f69e7-140">대상 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-140">Is the name of the destination database.</span></span>  
  
 <span data-ttu-id="f69e7-141">**-destinationtable** *destination_table*</span><span class="sxs-lookup"><span data-stu-id="f69e7-141">**-destinationtable** *destination_table*</span></span>  
 <span data-ttu-id="f69e7-142">대상 테이블의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-142">Is the name of the destination table.</span></span>  
  
 <span data-ttu-id="f69e7-143">**-destinationschema** *destination_schema_name*</span><span class="sxs-lookup"><span data-stu-id="f69e7-143">**-destinationschema** *destination_schema_name*</span></span>  
 <span data-ttu-id="f69e7-144">대상 테이블의 스키마 소유자입니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-144">The schema owner of the destination table.</span></span> <span data-ttu-id="f69e7-145">기본적으로 테이블 소유자를 dbo로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-145">By default, the table owner is assumed to be dbo.</span></span>  
  
 <span data-ttu-id="f69e7-146">**-destinationpassword** *destination_password*</span><span class="sxs-lookup"><span data-stu-id="f69e7-146">**-destinationpassword** *destination_password*</span></span>  
 <span data-ttu-id="f69e7-147">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 사용하여 대상 서버에 연결하는 데 사용되는 로그인 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-147">Is the password for the login used to connect to the destination server using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f69e7-148">가능하면 런타임 동안 보안 자격 증명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-148">When possible, supply security credentials at runtime.</span></span> <span data-ttu-id="f69e7-149">스크립트 파일에 자격 증명을 저장해야 하는 경우에는 무단으로 액세스하지 못하도록 파일에 보안을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-149">If you must store credentials in a script file, you should secure the file to prevent unauthorized access.</span></span>  
  
 <span data-ttu-id="f69e7-150">**-destinationuser** *destination_login*</span><span class="sxs-lookup"><span data-stu-id="f69e7-150">**-destinationuser** *destination_login*</span></span>  
 <span data-ttu-id="f69e7-151">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 사용하여 대상 서버에 연결하는 데 사용되는 로그인입니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-151">Is the login used to connect to the destination server using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="f69e7-152">*destination_login* 을 지정하지 않으면 대상 서버에 연결할 때 Windows 인증이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-152">If *destination_login* is not supplied, then Windows Authentication is used when connecting to the server.</span></span> [!INCLUDE[ssNoteWinAuthentication](../includes/ssnotewinauthentication-md.md)]  
  
 <span data-ttu-id="f69e7-153">**-destinationlocked**</span><span class="sxs-lookup"><span data-stu-id="f69e7-153">**-destinationlocked**</span></span>  
 <span data-ttu-id="f69e7-154">비교를 수행하는 동안 TABLOCK 및 HOLDLOCK 테이블 힌트를 사용하여 대상 테이블이 잠깁니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-154">The destination table is locked during the comparison using the TABLOCK and HOLDLOCK table hints.</span></span>  
  
 <span data-ttu-id="f69e7-155">**-b** *large_object_bytes*</span><span class="sxs-lookup"><span data-stu-id="f69e7-155">**-b** *large_object_bytes*</span></span>  
 <span data-ttu-id="f69e7-156">큰 개체 데이터 형식 열에 대해 비교할 바이트 수입니다. 이 데이터 형식에는 `text`, `ntext`, `image`, `varchar(max)`, `nvarchar(max)` 및 `varbinary(max)`가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-156">Is the number of bytes to compare for large object data type columns, which includes: `text`, `ntext`, `image`, `varchar(max)`, `nvarchar(max)` and `varbinary(max)`.</span></span> <span data-ttu-id="f69e7-157">*large_object_bytes* 는 기본적으로 열 크기로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-157">*large_object_bytes* defaults to the size of the column.</span></span> <span data-ttu-id="f69e7-158">*large_object_bytes* 에 지정한 바이트 수를 초과하는 데이터는 비교되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-158">Any data above *large_object_bytes* will not be compared.</span></span>  
  
 <span data-ttu-id="f69e7-159">**-bf**  *number_of_statements*</span><span class="sxs-lookup"><span data-stu-id="f69e7-159">**-bf**  *number_of_statements*</span></span>  
 <span data-ttu-id="f69e7-160">[!INCLUDE[tsql](../includes/tsql-md.md)] -f [!INCLUDE[tsql](../includes/tsql-md.md)] 옵션을 사용할 경우 현재 **스크립트 파일에 쓸** 문의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-160">Is the number of [!INCLUDE[tsql](../includes/tsql-md.md)] statements to write to the current [!INCLUDE[tsql](../includes/tsql-md.md)] script file when the **-f** option is used.</span></span> <span data-ttu-id="f69e7-161">[!INCLUDE[tsql](../includes/tsql-md.md)] 문의 수가 *number_of_statements*를 초과하면 새 [!INCLUDE[tsql](../includes/tsql-md.md)] 스크립트 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-161">When the number of [!INCLUDE[tsql](../includes/tsql-md.md)] statements exceeds *number_of_statements*, a new [!INCLUDE[tsql](../includes/tsql-md.md)] script file is created.</span></span>  
  
 <span data-ttu-id="f69e7-162">**-c**</span><span class="sxs-lookup"><span data-stu-id="f69e7-162">**-c**</span></span>  
 <span data-ttu-id="f69e7-163">열 수준에서 차이점을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-163">Compare column-level differences.</span></span>  
  
 <span data-ttu-id="f69e7-164">**-dt**</span><span class="sxs-lookup"><span data-stu-id="f69e7-164">**-dt**</span></span>  
 <span data-ttu-id="f69e7-165">*table_name*에 지정된 결과 테이블이 이미 있는 경우 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-165">Drop the result table specified by *table_name*, if the table already exists.</span></span>  
  
 <span data-ttu-id="f69e7-166">**-et** *table_name*</span><span class="sxs-lookup"><span data-stu-id="f69e7-166">**-et** *table_name*</span></span>  
 <span data-ttu-id="f69e7-167">만들 결과 테이블의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-167">Specifies the name of the result table to create.</span></span> <span data-ttu-id="f69e7-168">이 테이블이 이미 있을 경우 **-DT** 를 사용해야 합니다. 그렇지 않으면 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-168">If this table already exists, **-DT** must be used or the operation will fail.</span></span>  
  
 <span data-ttu-id="f69e7-169">**-f** [ *file_name* ]</span><span class="sxs-lookup"><span data-stu-id="f69e7-169">**-f** [ *file_name* ]</span></span>  
 <span data-ttu-id="f69e7-170">대상 서버의 테이블을 원본 서버의 테이블과 일치시키는 [!INCLUDE[tsql](../includes/tsql-md.md)] 스크립트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-170">Generates a [!INCLUDE[tsql](../includes/tsql-md.md)] script to bring the table at the destination server into convergence with the table at the source server.</span></span> <span data-ttu-id="f69e7-171">생성된 [!INCLUDE[tsql](../includes/tsql-md.md)] 스크립트 파일의 이름과 경로를 필요에 따라 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-171">You can optionally specify a name and path for the generated [!INCLUDE[tsql](../includes/tsql-md.md)] script file.</span></span> <span data-ttu-id="f69e7-172">*file_name* 을 지정하지 않으면 유틸리티가 실행되는 디렉터리에 [!INCLUDE[tsql](../includes/tsql-md.md)] 스크립트 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-172">If *file_name* is not specified, the [!INCLUDE[tsql](../includes/tsql-md.md)] script file is generated in the directory where the utility runs.</span></span>  
  
 <span data-ttu-id="f69e7-173">**-o** *output_file_name*</span><span class="sxs-lookup"><span data-stu-id="f69e7-173">**-o** *output_file_name*</span></span>  
 <span data-ttu-id="f69e7-174">출력 파일의 전체 이름 및 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-174">Is the full name and path of the output file.</span></span>  
  
 <span data-ttu-id="f69e7-175">**-q**</span><span class="sxs-lookup"><span data-stu-id="f69e7-175">**-q**</span></span>  
 <span data-ttu-id="f69e7-176">행 개수와 스키마만 비교하여 비교 작업을 빨리 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-176">Perform a fast comparison by only comparing row counts and schema.</span></span>  
  
 <span data-ttu-id="f69e7-177">**-rc** *number_of_retries*</span><span class="sxs-lookup"><span data-stu-id="f69e7-177">**-rc** *number_of_retries*</span></span>  
 <span data-ttu-id="f69e7-178">유틸리티가 실패한 작업을 다시 시도하는 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-178">Number of times that the utility retries a failed operation.</span></span>  
  
 <span data-ttu-id="f69e7-179">**-ri** *retry_interval*</span><span class="sxs-lookup"><span data-stu-id="f69e7-179">**-ri**  *retry_interval*</span></span>  
 <span data-ttu-id="f69e7-180">다시 시도 작업 사이의 대기 간격(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-180">Interval, in seconds, to wait between retries.</span></span>  
  
 <span data-ttu-id="f69e7-181">**-strict**</span><span class="sxs-lookup"><span data-stu-id="f69e7-181">**-strict**</span></span>  
 <span data-ttu-id="f69e7-182">원본 스키마와 대상 스키마를 엄격하게 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-182">Source and destination schema are strictly compared.</span></span>  
  
 <span data-ttu-id="f69e7-183">**-t** *connection_timeouts*</span><span class="sxs-lookup"><span data-stu-id="f69e7-183">**-t** *connection_timeouts*</span></span>  
 <span data-ttu-id="f69e7-184">원본 서버 및 대상 서버에 대한 연결 제한 시간(초)을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-184">Sets the connection timeout period, in seconds, for connections to the source server and destination server.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f69e7-185">Return Value</span><span class="sxs-lookup"><span data-stu-id="f69e7-185">Return Value</span></span>  
  
|<span data-ttu-id="f69e7-186">값</span><span class="sxs-lookup"><span data-stu-id="f69e7-186">Value</span></span>|<span data-ttu-id="f69e7-187">Description</span><span class="sxs-lookup"><span data-stu-id="f69e7-187">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f69e7-188">**0**</span><span class="sxs-lookup"><span data-stu-id="f69e7-188">**0**</span></span>|<span data-ttu-id="f69e7-189">Success</span><span class="sxs-lookup"><span data-stu-id="f69e7-189">Success</span></span>|  
|<span data-ttu-id="f69e7-190">**1**</span><span class="sxs-lookup"><span data-stu-id="f69e7-190">**1**</span></span>|<span data-ttu-id="f69e7-191">오류</span><span class="sxs-lookup"><span data-stu-id="f69e7-191">Critical error</span></span>|  
|<span data-ttu-id="f69e7-192">**2**</span><span class="sxs-lookup"><span data-stu-id="f69e7-192">**2**</span></span>|<span data-ttu-id="f69e7-193">테이블 차이</span><span class="sxs-lookup"><span data-stu-id="f69e7-193">Table differences</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f69e7-194">설명</span><span class="sxs-lookup"><span data-stu-id="f69e7-194">Remarks</span></span>  
 <span data-ttu-id="f69e7-195">비 서버에서는 **tablediff** 유틸리티를 사용할 수 없습니다 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f69e7-195">The **tablediff** utility cannot be used with non-[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] servers.</span></span>  
  
 <span data-ttu-id="f69e7-196">데이터 형식이 `sql_variant`인 열이 있는 테이블은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-196">Tables with `sql_variant` data type columns are not supported.</span></span>  
  
 <span data-ttu-id="f69e7-197">기본적으로 **tablediff** 유틸리티는 원본 열과 대상 열 간에 다음 데이터 형식 매핑을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-197">By default, the **tablediff** utility supports the following data type mappings between source and destination columns.</span></span>  
  
|<span data-ttu-id="f69e7-198">원본 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="f69e7-198">Source data type</span></span>|<span data-ttu-id="f69e7-199">대상 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="f69e7-199">Destination data type</span></span>|  
|----------------------|---------------------------|  
|`tinyint`|<span data-ttu-id="f69e7-200">`smallint`, `int` 또는 `bigint`</span><span class="sxs-lookup"><span data-stu-id="f69e7-200">`smallint`, `int`, or `bigint`</span></span>|  
|`smallint`|<span data-ttu-id="f69e7-201">`int` 또는 `bigint`</span><span class="sxs-lookup"><span data-stu-id="f69e7-201">`int` or `bigint`</span></span>|  
|`int`|`bigint`|  
|`timestamp`|`varbinary`|  
|`varchar(max)`|`text`|  
|`nvarchar(max)`|`ntext`|  
|`varbinary(max)`|`image`|  
|`text`|`varchar(max)`|  
|`ntext`|`nvarchar(max)`|  
|`image`|`varbinary(max)`|  
  
 <span data-ttu-id="f69e7-202">**-strict** 옵션을 사용하여 이러한 매핑을 허용하지 않고 유효성 검사를 엄격하게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-202">Use the **-strict** option to disallow these mappings and perform a strict validation.</span></span>  
  
 <span data-ttu-id="f69e7-203">비교할 원본 테이블에는 하나 이상의 기본 키, ID 또는 ROWGUID 열이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-203">The source table in the comparison must contain at least one primary key, identity, or ROWGUID column.</span></span> <span data-ttu-id="f69e7-204">**-strict** 옵션을 사용하는 경우에는 대상 테이블에도 기본 키, ID 또는 ROWGUID 열이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-204">When you use the **-strict** option, the destination table must also have a primary key, identity, or ROWGUID column.</span></span>  
  
 <span data-ttu-id="f69e7-205">대상 테이블을 일치시키기 위해 생성된 [!INCLUDE[tsql](../includes/tsql-md.md)] 스크립트에는 다음 데이터 형식이 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-205">The [!INCLUDE[tsql](../includes/tsql-md.md)] script generated to bring the destination table into convergence does not include the following data types:</span></span>  
  
-   `varchar(max)`  
  
-   `nvarchar(max)`  
  
-   `varbinary(max)`  
  
-   `timestamp`  
  
-   <span data-ttu-id="f69e7-206">**xml**</span><span class="sxs-lookup"><span data-stu-id="f69e7-206">**xml**</span></span>  
  
-   `text`  
  
-   `ntext`  
  
-   `image`  
  
## <a name="permissions"></a><span data-ttu-id="f69e7-207">사용 권한</span><span class="sxs-lookup"><span data-stu-id="f69e7-207">Permissions</span></span>  
 <span data-ttu-id="f69e7-208">테이블을 비교하려면 비교할 테이블 개체에 대한 SELECT ALL 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-208">To compare tables, you need SELECT ALL permissions on the table objects being compared.</span></span>  
  
 <span data-ttu-id="f69e7-209">**-et** 옵션을 사용하려면 db_owner 고정 데이터베이스 역할의 멤버이거나 적어도 구독 데이터베이스에 대한 CREATE TABLE 권한과 대상 서버의 대상 소유자 스키마에 대한 ALTER 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-209">To use the **-et** option, you must be a member of the db_owner fixed database role, or at least have CREATE TABLE permission in the subscription database and ALTER permission on the destination owner schema at the destination server.</span></span>  
  
 <span data-ttu-id="f69e7-210">**-dt** 옵션을 사용하려면 db_owner 고정 데이터베이스 역할의 멤버이거나 적어도 대상 서버의 대상 소유자 스키마에 대한 ALTER 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-210">To use the **-dt** option, you must be a member of the db_owner fixed database role, or at least have ALTER permission on the destination owner schema at the destination server.</span></span>  
  
 <span data-ttu-id="f69e7-211">**-o** 또는 **-f** 옵션을 사용하려면 지정된 파일 디렉터리 위치에 대한 쓰기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f69e7-211">To use the **-o** or **-f** options, you must have write permissions to the specified file directory location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f69e7-212">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f69e7-212">See Also</span></span>  
 [<span data-ttu-id="f69e7-213">복제된 테이블의 차이점 비교&#40;복제 프로그래밍&#41;</span><span class="sxs-lookup"><span data-stu-id="f69e7-213">Compare Replicated Tables for Differences &#40;Replication Programming&#41;</span></span>](../relational-databases/replication/administration/compare-replicated-tables-for-differences-replication-programming.md)  
  
  

---
title: bcp_control | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_control
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_control function
ms.assetid: 32187282-1385-4c52-9134-09f061eb44f5
author: rothja
ms.author: jroth
ms.openlocfilehash: 7ea5d60da8069707a53f3bdf2de53345cd11090f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638745"
---
# <a name="bcp_control"></a><span data-ttu-id="f7a7f-102">bcp_control</span><span class="sxs-lookup"><span data-stu-id="f7a7f-102">bcp_control</span></span>
  <span data-ttu-id="f7a7f-103">파일과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 간의 대량 복사에 대한 다양한 제어 매개 변수의 기본 설정을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-103">Changes the default settings for various control parameters for a bulk copy between a file and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7a7f-104">구문</span><span class="sxs-lookup"><span data-stu-id="f7a7f-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_control (  
HDBC   
hdbc  
,  
INT   
eOption  
,  
void*   
iValue  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="f7a7f-105">인수</span><span class="sxs-lookup"><span data-stu-id="f7a7f-105">Arguments</span></span>  
 <span data-ttu-id="f7a7f-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="f7a7f-106">*hdbc*</span></span>  
 <span data-ttu-id="f7a7f-107">대량 복사가 가능한 ODBC 연결 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="f7a7f-108">*eOption*</span><span class="sxs-lookup"><span data-stu-id="f7a7f-108">*eOption*</span></span>  
 <span data-ttu-id="f7a7f-109">다음 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-109">Is one of the following:</span></span>  
  
 <span data-ttu-id="f7a7f-110">BCPABORT</span><span class="sxs-lookup"><span data-stu-id="f7a7f-110">BCPABORT</span></span>  
 <span data-ttu-id="f7a7f-111">이미 진행 중인 대량 복사 작업을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-111">Stops a bulk-copy operation that is already in progress.</span></span> <span data-ttu-id="f7a7f-112">다른 스레드에서 BCPABORT의 *Eoption* 을 사용 하 여 **bcp_control** 를 호출 하 여 실행 중인 대량 복사 작업을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-112">Call **bcp_control** with an *eOption* of BCPABORT from another thread to stop a running bulk copy operation.</span></span> <span data-ttu-id="f7a7f-113">*Ivalue* 매개 변수는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-113">The *iValue* parameter is ignored.</span></span>  
  
 <span data-ttu-id="f7a7f-114">BCPBATCH</span><span class="sxs-lookup"><span data-stu-id="f7a7f-114">BCPBATCH</span></span>  
 <span data-ttu-id="f7a7f-115">일괄 처리당 행 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-115">Is the number of rows per batch.</span></span> <span data-ttu-id="f7a7f-116">기본값은 0으로, 데이터를 추출할 때 테이블에 있는 모든 행 수를 나타내거나 데이터를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 복사할 때 사용자 데이터 파일에 있는 모든 행 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-116">The default is 0, which indicates either all rows in a table, when data is being extracted, or all rows in the user data file, when data is being copied to an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f7a7f-117">1보다 작은 값을 지정하면 BCPBATCH가 기본값으로 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-117">A value less than 1 resets BCPBATCH to the default.</span></span>  
  
 <span data-ttu-id="f7a7f-118">BCPDELAYREADFMT</span><span class="sxs-lookup"><span data-stu-id="f7a7f-118">BCPDELAYREADFMT</span></span>  
 <span data-ttu-id="f7a7f-119">부울 값이 true로 설정 된 경우 실행 시 [bcp_readfmt](bcp-readfmt.md) 를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-119">A Boolean, if set to true, will cause [bcp_readfmt](bcp-readfmt.md) to read at execution.</span></span> <span data-ttu-id="f7a7f-120">False (기본값) 이면 bcp_readfmt는 서식 파일을 즉시 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-120">If false (the default), bcp_readfmt will immediately read the format file.</span></span> <span data-ttu-id="f7a7f-121">BCPDELAYREADFMT가 true이 고 bcp_columns 또는 bcp_setcolfmt를 호출 하면 시퀀스 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-121">A sequence error will occur if BCPDELAYREADFMT is true and you call bcp_columns or bcp_setcolfmt.</span></span>  
  
 <span data-ttu-id="f7a7f-122">`bcp_control(hdbc,` `, (void *)FALSE)` `bcp_control(hdbc,` Bcpdelayreadfmt 및 bcp_writefmt를 호출한 후 bcpdelayreadfmt를 호출 하는 경우에도 시퀀스 오류가 발생 합니다 `, (void *)TRUE)` .</span><span class="sxs-lookup"><span data-stu-id="f7a7f-122">A sequence error will also occur if you call `bcp_control(hdbc,` BCPDELAYREADFMT`, (void *)FALSE)` after calling `bcp_control(hdbc,` BCPDELAYREADFMT`, (void *)TRUE)` and bcp_writefmt.</span></span>  
  
 <span data-ttu-id="f7a7f-123">자세한 내용은 [메타데이터 검색](../native-client/features/metadata-discovery.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-123">For more information, see [Metadata Discovery](../native-client/features/metadata-discovery.md).</span></span>  
  
 <span data-ttu-id="f7a7f-124">BCPFILECP</span><span class="sxs-lookup"><span data-stu-id="f7a7f-124">BCPFILECP</span></span>  
 <span data-ttu-id="f7a7f-125">*Ivalue* 는 데이터 파일에 대 한 코드 페이지 번호를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-125">*iValue* contains the number of the code page for the data file.</span></span> <span data-ttu-id="f7a7f-126">1252나 850과 같은 코드 페이지 번호를 지정하거나 다음 값 중 하나를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-126">You can specify the number of the code page, such as 1252 or 850, or one of these values:</span></span>  
  
 <span data-ttu-id="f7a7f-127">BCPFILE_ACP: 파일의 데이터가 Microsoft Windows?</span><span class="sxs-lookup"><span data-stu-id="f7a7f-127">BCPFILE_ACP: data in the file is in the Microsoft Windows??</span></span> <span data-ttu-id="f7a7f-128">클라이언트의 코드 페이지입니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-128">code page of the client.</span></span>  
  
 <span data-ttu-id="f7a7f-129">BCPFILE_OEMCP: 파일의 데이터가 클라이언트의 OEM 코드 페이지에 있습니다(기본값).</span><span class="sxs-lookup"><span data-stu-id="f7a7f-129">BCPFILE_OEMCP: data in the file is in the OEM code page of the client (default).</span></span>  
  
 <span data-ttu-id="f7a7f-130">BCPFILE_RAW: 파일의 데이터가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 코드 페이지에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-130">BCPFILE_RAW: data in the file is in the code page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="f7a7f-131">BCPFILEFMT</span><span class="sxs-lookup"><span data-stu-id="f7a7f-131">BCPFILEFMT</span></span>  
 <span data-ttu-id="f7a7f-132">데이터 파일 형식의 버전 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-132">The version number of the data file format.</span></span> <span data-ttu-id="f7a7f-133">이 값은 80([!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]), 90([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]), 100([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 또는 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]), 110([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) 또는 120([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)])이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-133">This can be 80 ([!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]), 90 ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]), 100 ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]), 110 ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]), or 120 ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]).</span></span> <span data-ttu-id="f7a7f-134">기본값은 120입니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-134">120 is the default.</span></span> <span data-ttu-id="f7a7f-135">이 옵션은 이전 버전 서버에서 지원하는 형식으로 데이터를 가져오고 내보내는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-135">This is useful for exporting and importing data in formats that were supported by earlier version of the server.</span></span> <span data-ttu-id="f7a7f-136">예를 들어 서버의 텍스트 열에서 얻은 데이터를 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 이상 서버의 **varchar (max)** 열로 가져오려면 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 80을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-136">For example, to import data that was obtained from a text column in a [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] server into a **varchar(max)** column in a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later server, you should specify 80.</span></span> <span data-ttu-id="f7a7f-137">마찬가지로 **varchar (max)** 열에서 데이터를 내보낼 때 80을 지정 하면 텍스트 열이 형식으로 저장 되는 것 처럼 저장 되 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 고 서버의 텍스트 열로 가져올 수 있습니다 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f7a7f-137">Similarly, if you specify 80 when exporting data from a **varchar(max)** column, it will be saved just like text columns are saved in the [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] format, and can be imported into a text column of a [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] server.</span></span>  
  
 <span data-ttu-id="f7a7f-138">BCPFIRST</span><span class="sxs-lookup"><span data-stu-id="f7a7f-138">BCPFIRST</span></span>  
 <span data-ttu-id="f7a7f-139">복사할 파일이나 테이블의 첫 번째 데이터 행입니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-139">Is the first row of data to file or table to copy.</span></span> <span data-ttu-id="f7a7f-140">기본값은 1입니다. 1보다 작은 값을 지정하면 이 옵션은 기본값으로 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-140">The default is 1; a value less than 1 resets this option to its default.</span></span>  
  
 <span data-ttu-id="f7a7f-141">BCPFIRSTEX</span><span class="sxs-lookup"><span data-stu-id="f7a7f-141">BCPFIRSTEX</span></span>  
 <span data-ttu-id="f7a7f-142">BCP out 작업의 경우 데이터 파일에 복사할 데이터베이스 테이블의 첫 번째 행을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-142">For BCP out operations, specifies the first row of the database table to copy into the data file.</span></span>  
  
 <span data-ttu-id="f7a7f-143">BCP in 작업의 경우 데이터베이스 테이블에 복사할 데이터 파일의 첫 번째 행을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-143">For BCP in operations, specifies the first row of the data file to copy into the database table.</span></span>  
  
 <span data-ttu-id="f7a7f-144">*Ivalue* 매개 변수는 값을 포함 하는 부호 있는 64 비트 정수 주소 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-144">The *iValue* parameter is expected to be the address of a signed 64-bit integer containing the value.</span></span> <span data-ttu-id="f7a7f-145">BCPFIRSTEX에 전달할 수 있는 최대값은 2^63-1입니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-145">The maximum value that can be passed to BCPFIRSTEX is 2^63-1.</span></span>  
  
 <span data-ttu-id="f7a7f-146">BCPFMTXML</span><span class="sxs-lookup"><span data-stu-id="f7a7f-146">BCPFMTXML</span></span>  
 <span data-ttu-id="f7a7f-147">생성되는 서식 파일이 XML 형식이 되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-147">Specifies that the format file generated should be in XML format.</span></span> <span data-ttu-id="f7a7f-148">기본적으로 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-148">It is off by default.</span></span>  
  
 <span data-ttu-id="f7a7f-149">XML 서식 파일은 더 높은 유연성을 제공하지만 몇 가지 제약 조건이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-149">XML format files provide greater flexibility but with some added constraints.</span></span> <span data-ttu-id="f7a7f-150">예를 들어 이전 서식 파일에서는 가능했던 작업인 필드의 접두사와 종결자를 동시에 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-150">For example, you can not specify the prefix and terminator for a field simultaneously, which was possible in older format files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f7a7f-151">XML 서식 파일은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client와 함께 설치된 경우에만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-151">XML format files are only supported when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed along with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 <span data-ttu-id="f7a7f-152">BCPHINTS</span><span class="sxs-lookup"><span data-stu-id="f7a7f-152">BCPHINTS</span></span>  
 <span data-ttu-id="f7a7f-153">*Ivalue* 는 sqltchar 문자열 포인터를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-153">*iValue* contains an SQLTCHAR character string pointer.</span></span> <span data-ttu-id="f7a7f-154">주소가 지정된 문자열에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 대량 복사 처리 힌트나 결과 집합을 반환하는 Transact-SQL 문을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-154">The string addressed specifies either [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bulk-copy processing hints or a Transact-SQL statement that returns a result set.</span></span> <span data-ttu-id="f7a7f-155">Transact-SQL 문이 둘 이상의 결과 집합을 반환하도록 지정된 경우 첫 번째 결과 집합 다음에 오는 결과 집합은 모두 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-155">If a Transact-SQL statement is specified that returns more than one result set, all result sets after the first are ignored.</span></span> <span data-ttu-id="f7a7f-156">대량 복사 처리 힌트에 대 한 자세한 내용은 [Bcp 유틸리티](../../tools/bcp-utility.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-156">For more information about bulk-copy processing hints, see [bcp Utility](../../tools/bcp-utility.md).</span></span>  
  
 <span data-ttu-id="f7a7f-157">BCPKEEPIDENTITY</span><span class="sxs-lookup"><span data-stu-id="f7a7f-157">BCPKEEPIDENTITY</span></span>  
 <span data-ttu-id="f7a7f-158">*Ivalue* 가 TRUE 이면 대량 복사 함수에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identity 제약 조건으로 정의 된 열에 제공 된 데이터 값을 삽입 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-158">When *iValue* is TRUE, specifies that bulk copy functions insert data values supplied for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] columns defined with an identity constraint.</span></span> <span data-ttu-id="f7a7f-159">입력 파일은 ID 열에 해당하는 값을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-159">The input file must supply values for the identity columns.</span></span> <span data-ttu-id="f7a7f-160">설정되지 않은 경우 삽입된 행에 대해 새 ID 값이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-160">If this is not set, new identity values are generated for the inserted rows.</span></span> <span data-ttu-id="f7a7f-161">파일에서 ID 열에 대한 데이터는 모두 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-161">Any data present in the file for the identity columns is ignored.</span></span>  
  
 <span data-ttu-id="f7a7f-162">BCPKEEPNULLS</span><span class="sxs-lookup"><span data-stu-id="f7a7f-162">BCPKEEPNULLS</span></span>  
 <span data-ttu-id="f7a7f-163">파일의 빈 데이터 값을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에서 NULL 값으로 변환할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-163">Specifies whether empty data values in the file will be converted to NULL values in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="f7a7f-164">*Ivalue* 가 TRUE 이면 빈 값은 테이블에서 NULL로 변환 됩니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f7a7f-164">When *iValue* is TRUE, empty values will be converted to NULL in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="f7a7f-165">기본적으로 빈 값은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에서 열의 기본값(있는 경우)으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-165">The default is for empty values to be converted to a default value for the column in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table if a default exists.</span></span>  
  
 <span data-ttu-id="f7a7f-166">BCPLAST</span><span class="sxs-lookup"><span data-stu-id="f7a7f-166">BCPLAST</span></span>  
 <span data-ttu-id="f7a7f-167">복사할 마지막 행입니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-167">Is the last row to copy.</span></span> <span data-ttu-id="f7a7f-168">기본값은 모든 행 복사입니다. 1보다 작은 값을 지정하면 이 옵션은 기본값으로 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-168">The default is to copy all rows; a value less than 1 resets this option to its default.</span></span>  
  
 <span data-ttu-id="f7a7f-169">BCPLASTEX</span><span class="sxs-lookup"><span data-stu-id="f7a7f-169">BCPLASTEX</span></span>  
 <span data-ttu-id="f7a7f-170">BCP out 작업의 경우 데이터 파일에 복사할 데이터베이스 테이블의 마지막 행을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-170">For BCP out operations, specifies the last row of the database table to copy into the data file.</span></span>  
  
 <span data-ttu-id="f7a7f-171">BCP in 작업의 경우 데이터베이스 테이블에 복사할 데이터 파일의 마지막 행을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-171">For BCP in operations, specifies the last row of the data file to copy into the database table.</span></span>  
  
 <span data-ttu-id="f7a7f-172">*Ivalue* 매개 변수는 값을 포함 하는 부호 있는 64 비트 정수 주소 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-172">The *iValue* parameter is expected to be the address of a signed 64-bit integer containing the value.</span></span> <span data-ttu-id="f7a7f-173">BCPLASTEX에 전달할 수 있는 최대값은 2^63-1입니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-173">The maximum value that can be passed to BCPLASTEX is 2^63-1.</span></span>  
  
 <span data-ttu-id="f7a7f-174">BCPMAXERRS</span><span class="sxs-lookup"><span data-stu-id="f7a7f-174">BCPMAXERRS</span></span>  
 <span data-ttu-id="f7a7f-175">대량 복사 작업이 실패하기 전에 허용되는 오류 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-175">Is the number of errors allowed before the bulk copy operation fails.</span></span> <span data-ttu-id="f7a7f-176">기본값은 10입니다. 1 보다 작은 값은이 옵션을 기본값으로 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-176">The default is 10; a value less than 1 resets this option to its default.</span></span> <span data-ttu-id="f7a7f-177">대량 복사에는 최대 65,535개의 오류가 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-177">Bulk copy imposes a maximum of 65,535 errors.</span></span> <span data-ttu-id="f7a7f-178">이 옵션을 65,535보다 큰 값으로 설정하려고 하는 경우 이 옵션은 65,535로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-178">An attempt to set this option to a value larger than 65,535 results in the option being set to 65,535.</span></span>  
  
 <span data-ttu-id="f7a7f-179">BCPODBC</span><span class="sxs-lookup"><span data-stu-id="f7a7f-179">BCPODBC</span></span>  
 <span data-ttu-id="f7a7f-180">TRUE 이면 문자 형식으로 저장 된 **datetime** 및 **SMALLDATETIME** 값이 ODBC 타임 스탬프 이스케이프 시퀀스 접두사 및 접미사를 사용 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-180">When TRUE, specifies that **datetime** and **smalldatetime** values saved in character format will use the ODBC timestamp escape sequence prefix and suffix.</span></span> <span data-ttu-id="f7a7f-181">BCPODBC 옵션은 BCP_OUT에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-181">The BCPODBC option only applies to BCP_OUT.</span></span>  
  
 <span data-ttu-id="f7a7f-182">FALSE 인 경우 1997 년 1 월 1 일을 나타내는 **datetime** 값은 1997-01-01 00:00:00.000 문자열로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-182">When FALSE, a **datetime** value representing January 1, 1997 is converted to the character string: 1997-01-01 00:00:00.000.</span></span> <span data-ttu-id="f7a7f-183">TRUE 이면 동일한 **datetime** 값이 {ts ' 1997-01-01 00:00:00.000 '}로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-183">When TRUE, the same **datetime** value is represented as: {ts '1997-01-01 00:00:00.000'}.</span></span>  
  
 <span data-ttu-id="f7a7f-184">BCPROWCOUNT</span><span class="sxs-lookup"><span data-stu-id="f7a7f-184">BCPROWCOUNT</span></span>  
 <span data-ttu-id="f7a7f-185">현재(또는 마지막) BCP 작업에 의해 영향을 받는 행의 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-185">Returns the number of rows affected by the current (or last) BCP operation.</span></span>  
  
 <span data-ttu-id="f7a7f-186">BCPTEXTFILE</span><span class="sxs-lookup"><span data-stu-id="f7a7f-186">BCPTEXTFILE</span></span>  
 <span data-ttu-id="f7a7f-187">TRUE이면 데이터 파일이 이진 파일 대신 텍스트 파일이 되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-187">When TRUE, specifies that the data file is a text file, rather than a binary file.</span></span> <span data-ttu-id="f7a7f-188">파일이 텍스트 파일이면 BCP에서 데이터 파일의 처음 2바이트에서 유니코드 바이트 표식을 검사하여 텍스트 파일이 유니코드인지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-188">If the file is a text file, BCP determines whether or not it is Unicode by checking the Unicode byte marker in the first two bytes of the data file.</span></span>  
  
 <span data-ttu-id="f7a7f-189">BCPUNICODEFILE</span><span class="sxs-lookup"><span data-stu-id="f7a7f-189">BCPUNICODEFILE</span></span>  
 <span data-ttu-id="f7a7f-190">TRUE이면 입력 파일이 유니코드 파일이 되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-190">When TRUE, specifies the input file is a Unicode file.</span></span>  
  
 <span data-ttu-id="f7a7f-191">*iValue*</span><span class="sxs-lookup"><span data-stu-id="f7a7f-191">*iValue*</span></span>  
 <span data-ttu-id="f7a7f-192">지정 된 *Eoption*의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-192">Is the value for the specified *eOption*.</span></span> <span data-ttu-id="f7a7f-193">*Ivalue* 는 이후 64 비트 값으로 확장할 수 있도록 void 포인터로 캐스팅 되는 정수 (대기 시간) 값입니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-193">*iValue* is an integer (LONGLONG) value cast to a void pointer to allow for future expansion to 64 bit values.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="f7a7f-194">반환</span><span class="sxs-lookup"><span data-stu-id="f7a7f-194">Returns</span></span>  
 <span data-ttu-id="f7a7f-195">SUCCEED 또는 FAIL</span><span class="sxs-lookup"><span data-stu-id="f7a7f-195">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7a7f-196">설명</span><span class="sxs-lookup"><span data-stu-id="f7a7f-196">Remarks</span></span>  
 <span data-ttu-id="f7a7f-197">이 함수는 대량 복사를 취소하기 전에 허용되는 오류 수, 데이터 파일에서 복사할 첫 번째 행과 마지막 행의 번호 및 일괄 처리 크기를 비롯하여 대량 복사 작업에 대한 여러 가지 제어 매개 변수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-197">This function sets various control parameters for bulk-copy operations, including the number of errors allowed before canceling a bulk copy, the numbers of the first and last rows to copy from a data file, and the batch size.</span></span>  
  
 <span data-ttu-id="f7a7f-198">또한 이 함수는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 SELECT의 결과 집합을 대량 복사할 때 SELECT 문을 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-198">This function is also used to specify the SELECT statement when bulk copying out from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] the result set of a SELECT.</span></span> <span data-ttu-id="f7a7f-199">*Eoption* 을 BCPHINTS로 설정 하 고 SELECT 문을 포함 하는 sqltchar 문자열에 대 한 포인터를 갖도록 *ivalue* 를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-199">Set *eOption* to BCPHINTS and set *iValue* to have a pointer to an SQLTCHAR string containing the SELECT statement.</span></span>  
  
 <span data-ttu-id="f7a7f-200">이러한 제어 매개 변수는 사용자 파일과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블 간에 복사하는 경우에만 의미가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-200">These control parameters are only meaningful when copying between a user file and an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="f7a7f-201">Bcp_sendrow로 복사 되는 행에는 컨트롤 매개 변수 설정이 적용 되지 않습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [bcp_sendrow](bcp-sendrow.md)</span><span class="sxs-lookup"><span data-stu-id="f7a7f-201">Control parameter settings have no effect on rows copied to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with [bcp_sendrow](bcp-sendrow.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7a7f-202">예제</span><span class="sxs-lookup"><span data-stu-id="f7a7f-202">Example</span></span>  
  
```  
// Variables like henv not specified.  
SQLHDBC      hdbc;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, _T("address"), _T("address.add"), _T("addr.err"),  
   DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set the number of rows per batch.   
if (bcp_control(hdbc, BCPBATCH, (void*) 1000) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set file column count.   
if (bcp_columns(hdbc, 1) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set the file format.   
if (bcp_colfmt(hdbc, 1, 0, 0, SQL_VARLEN_DATA, '\n', 1, 1)  
   == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Execute the bulk copy.   
if (bcp_exec(hdbc, &nRowsProcessed) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
printf_s("%ld rows processed by bulk copy.", nRowsProcessed);  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="f7a7f-203">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f7a7f-203">See Also</span></span>  
 [<span data-ttu-id="f7a7f-204">Bulk Copy Functions</span><span class="sxs-lookup"><span data-stu-id="f7a7f-204">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

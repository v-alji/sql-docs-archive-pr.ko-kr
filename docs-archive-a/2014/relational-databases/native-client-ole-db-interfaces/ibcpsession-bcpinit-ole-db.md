---
title: IBCPSession::BCPInit(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPInit (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPInit method
ms.assetid: 583096d7-da34-49be-87fd-31210aac81aa
author: rothja
ms.author: jroth
ms.openlocfilehash: 25a01c71811de9d47ce01714402460bb53d4c70e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730632"
---
# <a name="ibcpsessionbcpinit-ole-db"></a><span data-ttu-id="19ee5-102">IBCPSession::BCPInit(OLE DB)</span><span class="sxs-lookup"><span data-stu-id="19ee5-102">IBCPSession::BCPInit (OLE DB)</span></span>
  <span data-ttu-id="19ee5-103">대량 복사 구조를 초기화하고, 일부 오류 검사를 수행하고, 데이터 및 서식 파일 이름이 올바른지 확인한 다음 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-103">Initializes the bulk copy structure, performs some error checking, verifies that the data and format file names are correct, and then opens them.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19ee5-104">구문</span><span class="sxs-lookup"><span data-stu-id="19ee5-104">Syntax</span></span>  
  
```  
  
HRESULT BCPInit(   
const wchar_t *pwszTable,  
const wchar_t *pwszDataFile,  
const wchar_t *pwszErrorFile,  
inteDirection);  
```  
  
## <a name="remarks"></a><span data-ttu-id="19ee5-105">설명</span><span class="sxs-lookup"><span data-stu-id="19ee5-105">Remarks</span></span>  
 <span data-ttu-id="19ee5-106">**BCPInit** 메서드는 다른 대량 복사 메서드를 호출하기 전에 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-106">The **BCPInit** method should be called before any other bulk-copy method.</span></span> <span data-ttu-id="19ee5-107">**BCPInit** 메서드는 워크스테이션과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 간의 데이터 대량 복사에 필요한 초기화를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-107">The **BCPInit** method performs the necessary initializations for a bulk copy of data between the workstation and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="19ee5-108">**BCPInit** 메서드는 데이터 파일이 아니라 데이터베이스 원본 또는 대상 테이블의 구조를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-108">The **BCPInit** method examines the structure of the database source or target table, not the data file.</span></span> <span data-ttu-id="19ee5-109">또한 데이터베이스 테이블, 뷰 또는 SELECT 결과 집합에 있는 각 열을 기반으로 데이터 파일의 데이터 형식 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-109">It specifies data format values for the data file based on each column in the database table, view, or SELECT result set.</span></span> <span data-ttu-id="19ee5-110">이 지정에는 각 열의 데이터 형식, 데이터에 길이 또는 Null 표시자 및 종결자 바이트 문자열이 있는지 여부, 고정 길이 데이터 형식의 길이가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-110">This specification includes the data type of each column, the presence or absence of a length or null indicator and terminator byte strings in the data, and the width of fixed-length data types.</span></span> <span data-ttu-id="19ee5-111">**BCPInit** 메서드는 이러한 값을 다음과 같이 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-111">The **BCPInit** method sets these values as follows:</span></span>  
  
-   <span data-ttu-id="19ee5-112">지정되는 데이터 형식은 데이터베이스 테이블, 뷰 또는 SELECT 결과 집합에 있는 열의 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-112">The data type specified is the data type of the column in the database table, view, or SELECT result set.</span></span> <span data-ttu-id="19ee5-113">데이터 형식은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client 헤더 파일 (sqlncli)에 지정 된 네이티브 데이터 형식으로 열거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-113">The data type is enumerated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native data types specified in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client header file (sqlncli.h).</span></span> <span data-ttu-id="19ee5-114">이 값은 BCP_TYPE_XXX 패턴을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-114">Their values are in the pattern of BCP_TYPE_XXX.</span></span> <span data-ttu-id="19ee5-115">데이터는 해당 컴퓨터 형식으로 표현됩니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-115">The data is represented in its computer form.</span></span> <span data-ttu-id="19ee5-116">즉, integer 데이터 형식의 열에서 가져온 데이터는 데이터 파일을 만든 컴퓨터에 따라 Big Endian 또는 Little Endian인 4바이트 시퀀스로 표현됩니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-116">That is, data from a column of integer data type is represented by a four-byte sequence that is big-or little-endian based on the computer that created the data file.</span></span>  
  
-   <span data-ttu-id="19ee5-117">데이터베이스 데이터 형식의 길이가 고정된 경우 데이터 파일 데이터의 길이도 고정됩니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-117">If a database data type is fixed in length, the data file data is also fixed in length.</span></span> <span data-ttu-id="19ee5-118">데이터를 처리하는 대량 복사 메서드(예: [IBCPSession::BCPExec](ibcpsession-bcpexec-ole-db.md))는 데이터 파일에 있는 데이터의 길이가 데이터베이스 테이블, 뷰 또는 SELECT 열 목록에 지정된 데이터의 길이와 동일할 것이라 예상하고 데이터 행을 구문 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-118">Bulk-copy methods that process data (for example, [IBCPSession::BCPExec](ibcpsession-bcpexec-ole-db.md)) parse data rows expecting the length of the data in the data file to be identical to the length of the data specified in the database table, view, or SELECT column list.</span></span> <span data-ttu-id="19ee5-119">예를 들어 `char(13)`로 정의된 데이터베이스 열의 데이터에서 파일의 각 데이터 행은 13자로 표현되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-119">For example, data for a database column defined as `char(13)` must be represented by 13 characters for each row of data in the file.</span></span> <span data-ttu-id="19ee5-120">데이터베이스 열이 Null 값을 허용하는 경우에는 고정 길이 데이터 앞에 Null 표시자를 붙일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-120">Fixed-length data can be prefixed with a null indicator if the database column allows null values.</span></span>  
  
-   <span data-ttu-id="19ee5-121">데이터를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 복사하는 경우 데이터 파일에 데이터베이스 테이블의 각 열에 대한 데이터가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-121">When copying data to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the data file must have data for each column in the database table.</span></span> <span data-ttu-id="19ee5-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 데이터를 복사하는 경우 데이터베이스 테이블, 뷰 또는 SELECT 결과 집합에 있는 모든 열의 데이터가 데이터 파일로 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-122">When copying data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], data from all columns in the database table, view, or SELECT result set are copied to the data file.</span></span>  
  
-   <span data-ttu-id="19ee5-123">데이터를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 복사하는 경우 데이터 파일에 있는 열의 서수 위치가 데이터베이스 테이블에 있는 열의 서수 위치와 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-123">When copying data to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the ordinal position of a column in the data file must be identical to the ordinal position of the column in the database table.</span></span> <span data-ttu-id="19ee5-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 데이터를 복사하는 경우 **BCPExec** 메서드는 데이터베이스 테이블에 있는 열의 서수 위치를 기반으로 데이터를 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-124">When copying data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the **BCPExec** method places data based on the ordinal position of the column in the database table.</span></span>  
  
-   <span data-ttu-id="19ee5-125">데이터베이스 데이터 형식의 길이가 가변적(예: `varbinary(22)`)이거나 데이터베이스 열이 Null 값을 포함할 수 있는 경우 데이터 파일의 데이터 앞에 길이/Null 표시자가 옵니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-125">If a database data type is variable in length (for example, `varbinary(22)`) or if a database column can contain null values, data in the data file is prefixed by a length/null indicator.</span></span> <span data-ttu-id="19ee5-126">표시자의 길이는 데이터 형식 및 대량 복사 버전에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-126">The width of the indicator varies based on the data type and version of bulk copy.</span></span> <span data-ttu-id="19ee5-127">[IBCPSession::BCPControl](ibcpsession-bcpcontrol-ole-db.md) 메서드 옵션 BCP_OPTION_FILEFMT는 데이터에 있는 표시자의 너비가 예상보다 짧은 경우를 표시하여 이후 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 실행하는 서버와 이전 대량 복사 데이터 파일 간의 호환성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-127">The [IBCPSession::BCPControl](ibcpsession-bcpcontrol-ole-db.md) method option BCP_OPTION_FILEFMT provides compatibility between earlier bulk-copy data files and servers running later versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by indicating when the width of indicators in the data is narrower than expected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19ee5-128">데이터 파일에 대해 지정된 데이터 형식 값을 변경하려면 [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) 및 [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-128">To change the data format values specified for a data file, use the [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) and [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) methods.</span></span>  
  
 <span data-ttu-id="19ee5-129">데이터베이스 옵션 **select into/bulkcopy**를 설정하면 인덱스가 없는 테이블에 대해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로의 대량 복사를 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-129">Bulk copies to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can be optimized for tables that do not contain indexes by setting the database option **select into/bulkcopy**.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="19ee5-130">인수</span><span class="sxs-lookup"><span data-stu-id="19ee5-130">Arguments</span></span>  
 <span data-ttu-id="19ee5-131">*pwszTable*[in]</span><span class="sxs-lookup"><span data-stu-id="19ee5-131">*pwszTable*[in]</span></span>  
 <span data-ttu-id="19ee5-132">복사의 원본 또는 대상이 될 데이터베이스 테이블의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-132">The name of the database table to be copied into or out of.</span></span> <span data-ttu-id="19ee5-133">이 이름은 데이터베이스 이름 또는 소유자 이름을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-133">The name can include the database name or the owner name.</span></span> <span data-ttu-id="19ee5-134">예를 들면 "pubs.username.titles", "pubs..titles", "username.titles"와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-134">For example, "pubs.username.titles", "pubs..titles", "username.titles".</span></span>  
  
 <span data-ttu-id="19ee5-135">eDirection 인수가 BCP_DIRECTION_OUT으로 설정된 경우 pwszTable 인수는 데이터베이스 뷰의 이름일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-135">If the eDirection argument is set to BCP_DIRECTION_OUT, the pwszTable argument can be the name of a database view.</span></span>  
  
 <span data-ttu-id="19ee5-136">eDirection 인수를 BCP_DIRECTION_OUT으로 설정하고 **BCPControl** 메서드가 호출되기 전에 **BCPExec** 메서드를 사용하여 SELECT 문을 지정한 경우 *pwszTable* 인수를 NULL로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-136">If the eDirection argument is set to BCP_DIRECTION_OUT and a SELECT statement is specified using the **BCPControl** method before the **BCPExec** method is called, the *pwszTable* argument must be set to NULL.</span></span>  
  
 <span data-ttu-id="19ee5-137">*pwszDataFile*[in]</span><span class="sxs-lookup"><span data-stu-id="19ee5-137">*pwszDataFile*[in]</span></span>  
 <span data-ttu-id="19ee5-138">복사의 원본 또는 대상이 될 사용자 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-138">The name of the user file to be copied into or out of.</span></span>  
  
 <span data-ttu-id="19ee5-139">*pwszErrorFile*[in]</span><span class="sxs-lookup"><span data-stu-id="19ee5-139">*pwszErrorFile*[in]</span></span>  
 <span data-ttu-id="19ee5-140">진행 메시지, 오류 메시지 및 어떤 이유로든 사용자 파일에서 테이블로 복사하지 못한 모든 행의 복사본으로 채워질 오류 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-140">The name of the error file to be filled with progress messages, error messages, and copies of any rows that could not be copied from a user file to a table.</span></span> <span data-ttu-id="19ee5-141">*pwszErrorFile* 인수를 NULL로 설정하면 오류 파일이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-141">If the *pwszErrorFile* argument is set to NULL, no error file is used.</span></span>  
  
 <span data-ttu-id="19ee5-142">*eDirection*[in]</span><span class="sxs-lookup"><span data-stu-id="19ee5-142">*eDirection*[in]</span></span>  
 <span data-ttu-id="19ee5-143">복사 작업의 방향(BCP_DIRECTION_IN 또는 BCP_DIRECTION _OUT)입니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-143">The direction of the copy operation, either BCP_DIRECTION_IN or BCP_DIRECTION _OUT.</span></span> <span data-ttu-id="19ee5-144">BCP_DIRECTION _IN은 사용자 파일에서 데이터베이스 테이블로의 복사본을 나타내고, BCP_DIRECTION _OUT은 데이터베이스 테이블에서 사용자 파일로의 복사본을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-144">BCP_DIRECTION _IN indicates a copy from a user file to a database table; BCP_DIRECTION _OUT indicates a copy from a database table to a user file.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="19ee5-145">반환 코드 값</span><span class="sxs-lookup"><span data-stu-id="19ee5-145">Return Code Values</span></span>  
 <span data-ttu-id="19ee5-146">S_OK</span><span class="sxs-lookup"><span data-stu-id="19ee5-146">S_OK</span></span>  
 <span data-ttu-id="19ee5-147">메서드가 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-147">The method succeeded.</span></span>  
  
 <span data-ttu-id="19ee5-148">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="19ee5-148">E_FAIL</span></span>  
 <span data-ttu-id="19ee5-149">공급자별 오류가 발생 했습니다. 자세한 내용은 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) 인터페이스를 사용 하십시오.</span><span class="sxs-lookup"><span data-stu-id="19ee5-149">A provider specific error occurred' for detailed information, use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="19ee5-150">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="19ee5-150">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="19ee5-151">메모리 부족 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-151">Out-of-memory error.</span></span>  
  
 <span data-ttu-id="19ee5-152">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="19ee5-152">E_INVALIDARG</span></span>  
 <span data-ttu-id="19ee5-153">하나 이상의 인수가 잘못 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-153">One or more of the arguments was not correctly specified.</span></span> <span data-ttu-id="19ee5-154">예를 들어 잘못된 파일 이름이 제공되었습니다.</span><span class="sxs-lookup"><span data-stu-id="19ee5-154">For example, an invalid file name was given.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19ee5-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="19ee5-155">See Also</span></span>  
 <span data-ttu-id="19ee5-156">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="19ee5-156">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span></span>  
 [<span data-ttu-id="19ee5-157">대량 복사 작업 수행</span><span class="sxs-lookup"><span data-stu-id="19ee5-157">Performing Bulk Copy Operations</span></span>](../native-client/features/performing-bulk-copy-operations.md)  
  
  

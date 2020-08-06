---
title: bcp_colfmt | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_colfmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_colfmt function
ms.assetid: 5c3b6299-80c7-4e84-8e69-4ff33009548e
author: rothja
ms.author: jroth
ms.openlocfilehash: f646f3aaf9a8f640d829020bd6762c07c406b61f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742016"
---
# <a name="bcp_colfmt"></a><span data-ttu-id="d8c05-102">bcp_colfmt</span><span class="sxs-lookup"><span data-stu-id="d8c05-102">bcp_colfmt</span></span>
  <span data-ttu-id="d8c05-103">사용자 파일에 있는 데이터의 원본 또는 대상 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-103">Specifies the source or target format of the data in a user file.</span></span> <span data-ttu-id="d8c05-104">원본 형식으로 사용될 경우 **bcp_colfmt** 는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블로의 대량 복사에서 데이터 원본으로 사용되는 기존 데이터 파일의 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-104">When used as a source format, **bcp_colfmt** specifies the format of an existing data file used as the source of data in a bulk copy to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="d8c05-105">대상 형식으로 사용될 경우에는 데이터 파일이 **bcp_colfmt**에 지정된 열 형식을 사용하여 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-105">When used as a target format, the data file is created using the column formats specified with **bcp_colfmt**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8c05-106">구문</span><span class="sxs-lookup"><span data-stu-id="d8c05-106">Syntax</span></span>  
  
```  
  
RETCODE bcp_colfmt (  
HDBC   
hdbc  
,  
INT  
idxUserDataCol  
,  
BYTE   
eUserDataType  
,  
INT   
cbIndicator  
,  
DBINT   
cbUserData  
,  
LPCBYTE   
pUserDataTerm  
,  
INT   
cbUserDataTerm  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="d8c05-107">인수</span><span class="sxs-lookup"><span data-stu-id="d8c05-107">Arguments</span></span>  
 <span data-ttu-id="d8c05-108">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="d8c05-108">*hdbc*</span></span>  
 <span data-ttu-id="d8c05-109">대량 복사가 가능한 ODBC 연결 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-109">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="d8c05-110">*idxUserDataCol*</span><span class="sxs-lookup"><span data-stu-id="d8c05-110">*idxUserDataCol*</span></span>  
 <span data-ttu-id="d8c05-111">형식이 지정되는 사용자 데이터 파일의 서수 열 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-111">Is the ordinal column number in the user data file for which the format is being specified.</span></span> <span data-ttu-id="d8c05-112">첫 번째 열은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-112">The first column is 1.</span></span>  
  
 <span data-ttu-id="d8c05-113">*eUserDataType*</span><span class="sxs-lookup"><span data-stu-id="d8c05-113">*eUserDataType*</span></span>  
 <span data-ttu-id="d8c05-114">사용자 파일에 있는 이 열의 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-114">Is the data type of this column in the user file.</span></span> <span data-ttu-id="d8c05-115">데이터베이스 테이블에 있는 해당 열의 데이터 형식(*idxServerColumn*)과 다르면 가능한 경우 대량 복사에서 데이터를 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-115">If different from the data type of the corresponding column in the database table (*idxServerColumn*), bulk copy converts the data if possible.</span></span>  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<span data-ttu-id="d8c05-116">에서는 *Euserdatatype* 매개 변수의 SQLXML 및 sqludt 데이터 형식 토큰에 대 한 지원이 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-116">introduced support for SQLXML and SQLUDT data type tokens in the *eUserDataType* parameter.</span></span>  
  
 <span data-ttu-id="d8c05-117">*eUserDataType* 매개 변수는 ODBC C 데이터 형식 열거자가 아닌 sqlncli.h의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식 토큰에 의해 열거됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-117">The *eUserDataType* parameter is enumerated by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type tokens in sqlncli.h, not the ODBC C data type enumerators.</span></span> <span data-ttu-id="d8c05-118">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 관련된 SQLCHARACTER 형식을 사용하여 ODBC 유형 SQL_C_CHAR라는 문자열을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-118">For example, you can specify a character string, ODBC type SQL_C_CHAR, using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific type SQLCHARACTER.</span></span>  
  
 <span data-ttu-id="d8c05-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식에 대한 기본 데이터 표현을 지정하려면 이 매개 변수를 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-119">To specify the default data representation for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type, set this parameter to 0.</span></span>  
  
 <span data-ttu-id="d8c05-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 파일로의 대량 복사에서 *eUserDataType* 이 SQLDECIMAL 또는 SQLNUMERIC인 경우</span><span class="sxs-lookup"><span data-stu-id="d8c05-120">For a bulk copy out of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] into a file, when *eUserDataType* is SQLDECIMAL or SQLNUMERIC:</span></span>  
  
-   <span data-ttu-id="d8c05-121">원본 열이 **decimal** 또는 **numeric**이 아니면 기본 전체 자릿수 및 소수 자릿수가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-121">If the source column is not **decimal** or **numeric**, the default precision and scale are used.</span></span>  
  
-   <span data-ttu-id="d8c05-122">원본 열이 **decimal** 또는 **numeric**이면 원본 열의 전체 자릿수와 소수 자릿수가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-122">If the source column is **decimal** or **numeric**, the precision and scale of the source column are used.</span></span>  
  
 <span data-ttu-id="d8c05-123">*cbIndicator*</span><span class="sxs-lookup"><span data-stu-id="d8c05-123">*cbIndicator*</span></span>  
 <span data-ttu-id="d8c05-124">열 데이터의 길이 또는 Null 표시기의 길이(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-124">Is the length, in bytes, of a length/null indicator within the column data.</span></span> <span data-ttu-id="d8c05-125">올바른 표시기 길이 값은 0(표시기를 사용하지 않을 경우), 1, 2, 4 또는 8입니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-125">Valid indicator length values are 0 (when using no indicator), 1, 2, 4, or 8.</span></span>  
  
 <span data-ttu-id="d8c05-126">기본 대량 복사 표시기를 사용하도록 지정하려면 이 매개 변수를 SQL_VARLEN_DATA로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-126">To specify default bulk copy indicator usage, set this parameter to SQL_VARLEN_DATA.</span></span>  
  
 <span data-ttu-id="d8c05-127">표시기는 메모리에서는 임의의 데이터 바로 앞에 나타나고 데이터 파일에서는 표시기가 적용되는 데이터 바로 앞에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-127">Indicators appear in memory directly before any data, and in the data file directly before the data to which they apply.</span></span>  
  
 <span data-ttu-id="d8c05-128">표시기와 최대 열 길이를 사용하거나 표시기와 종결자 시퀀스를 사용하는 등 두 가지 이상의 방법을 사용하여 데이터 파일 열 길이를 지정하는 경우 대량 복사에는 복사되는 데이터 크기가 가장 작은 방법이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-128">If more than one means of specifying a data file column length is used (such as an indicator and a maximum column length, or an indicator and a terminator sequence), bulk copy chooses the one that results in the least amount of data being copied.</span></span>  
  
 <span data-ttu-id="d8c05-129">사용자 개입을 통해 데이터 형식이 조정되지 않는 대량 복사로 생성된 데이터 파일에는 열 데이터의 길이가 변경될 수 있거나 열이 NULL 값을 허용할 수 있는 경우 표시기가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-129">Data files generated by bulk copy when no user intervention adjusts the format of the data contain indicators when the column data can vary in length or the column can accept NULL as a value.</span></span>  
  
 <span data-ttu-id="d8c05-130">*cbUserData*</span><span class="sxs-lookup"><span data-stu-id="d8c05-130">*cbUserData*</span></span>  
 <span data-ttu-id="d8c05-131">길이 표시기나 종결자의 길이를 제외한 사용자 파일에 있는 이 열 데이터의 최대 길이(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-131">Is the maximum length, in bytes, of this column's data in the user file, not including the length of any length indicator or terminator.</span></span>  
  
 <span data-ttu-id="d8c05-132">*cbUserData* 를 SQL_NULL_DATA로 설정하면 데이터 파일 열의 모든 값이 NULL이거나 NULL로 설정해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-132">Setting *cbUserData* to SQL_NULL_DATA indicates that all values in the data file column are, or should be set to NULL.</span></span>  
  
 <span data-ttu-id="d8c05-133">*cbUserData* 를 SQL_VARLEN_DATA로 설정하면 시스템에서 각 열의 데이터 길이를 확인함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-133">Setting *cbUserData* to SQL_VARLEN_DATA indicates that the system should determine the length of data in each column.</span></span> <span data-ttu-id="d8c05-134">일부 열의 경우 이 설정은 길이 또는 Null 표시기가 생성되어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 복사되는 복사본의 데이터 앞에 추가됨을 의미하거나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 복사되는 데이터에 표시기가 필요함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-134">For some columns, this could mean that a length/null indicator is generated to precede data on a copy from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or that the indicator is expected in data copied to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d8c05-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 문자 및 이진 데이터 형식의 경우 *cbUserData* 는 SQL_VARLEN_DATA, SQL_NULL_DATA, 0 또는 양수 값일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-135">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character and binary data types, *cbUserData* can be SQL_VARLEN_DATA, SQL_NULL_DATA, 0, or some positive value.</span></span> <span data-ttu-id="d8c05-136">*cbUserData* 가 SQL_VARLEN_DATA이면 시스템에서 길이 표시기(있는 경우)나 종결자 시퀀스를 사용하여 데이터 길이를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-136">If *cbUserData* is SQL_VARLEN_DATA, the system uses either the length indicator, if present, or a terminator sequence to determine the length of the data.</span></span> <span data-ttu-id="d8c05-137">길이 표시기와 종결자 시퀀스를 모두 지정하는 경우 대량 복사에는 복사되는 데이터 크기가 가장 작은 방법이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-137">If both a length indicator and a terminator sequence are supplied, bulk copy uses the one that results in the least amount of data being copied.</span></span> <span data-ttu-id="d8c05-138">*cbUserData* 가 SQL_VARLEN_DATA인 경우 열의 데이터 형식은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 문자 또는 이진 형식이며 길이 표시기나 종결자 시퀀스를 모두 지정하지 않으면 시스템에서 오류 메시지를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-138">If *cbUserData* is SQL_VARLEN_DATA, the data type is an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character or binary type, and neither a length indicator nor a terminator sequence is specified, the system returns an error message.</span></span>  
  
 <span data-ttu-id="d8c05-139">*cbUserData* 가 0이거나 양수 값이면 시스템은 *cbUserData* 를 최대 데이터 길이로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-139">If *cbUserData* is 0 or a positive value, the system uses *cbUserData* as the maximum data length.</span></span> <span data-ttu-id="d8c05-140">그러나 *cbUserData*가 양수이고 길이 표시자 또는 종결자 시퀀스도 제공되는 경우 시스템은 복사할 데이터가 적은 방법을 사용하여 데이터 길이를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-140">However, if, in addition to a positive *cbUserData*, a length indicator or terminator sequence is provided, the system determines the data length by using the method that results in the least amount of data being copied.</span></span>  
  
 <span data-ttu-id="d8c05-141">*cbUserData* 값은 데이터의 바이트 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-141">The *cbUserData* value represents the count of bytes of data.</span></span> <span data-ttu-id="d8c05-142">문자 데이터가 유니코드 와이드 문자로 표현되는 경우 양수 *cbUserData* 매개 변수 값은 문자 수와 각 문자의 바이트 크기를 곱한 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-142">If character data is represented by Unicode wide characters, then a positive *cbUserData* parameter value represents the number of characters multiplied by the size, in bytes, of each character.</span></span>  
  
 <span data-ttu-id="d8c05-143">*pUserDataTerm*</span><span class="sxs-lookup"><span data-stu-id="d8c05-143">*pUserDataTerm*</span></span>  
 <span data-ttu-id="d8c05-144">이 열에 사용할 종결자 시퀀스입니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-144">Is the terminator sequence to be used for this column.</span></span> <span data-ttu-id="d8c05-145">이 매개 변수는 주로 문자 데이터 형식에 유용한데 그 이유는 다른 모든 형식은 길이가 고정되어 있거나 이진 데이터의 경우 현재 바이트 수를 정확하게 기록하기 위해 길이 표시기가 필요하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-145">This parameter is useful mainly for character data types because all other types are of fixed length or, in the case of binary data, require an indicator of length to accurately record the number of bytes present.</span></span>  
  
 <span data-ttu-id="d8c05-146">추출한 데이터가 종결되지 않도록 하거나 사용자 파일의 데이터가 종결되지 않았음을 나타내려면 이 매개 변수를 NULL로 설정하십시오.</span><span class="sxs-lookup"><span data-stu-id="d8c05-146">To avoid terminating extracted data, or to indicate that data in a user file is not terminated, set this parameter to NULL.</span></span>  
  
 <span data-ttu-id="d8c05-147">종결자와 길이 표시기를 사용하거나 종결자와 최대 열 길이를 사용하는 등 두 가지 이상의 방법을 사용하여 사용자 파일 열 길이를 지정하는 경우 대량 복사에는 복사되는 데이터 크기가 가장 작은 방법이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-147">If more than one means of specifying a user-file column length is used (such as a terminator and a length indicator, or a terminator and a maximum column length), bulk copy chooses the one that results in the least amount of data being copied.</span></span>  
  
 <span data-ttu-id="d8c05-148">대량 복사 API는 필요한 경우 유니코드에서 MBCS로의 문자 변환을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-148">The bulk copy API performs Unicode-to-MBCS character conversion as required.</span></span> <span data-ttu-id="d8c05-149">종결자 바이트 문자열 및 바이트 문자열 길이가 모두 올바르게 설정되도록 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-149">Care must be taken to ensure that both the terminator byte string and the length of the byte string are set correctly.</span></span>  
  
 <span data-ttu-id="d8c05-150">*cbUserDataTerm*</span><span class="sxs-lookup"><span data-stu-id="d8c05-150">*cbUserDataTerm*</span></span>  
 <span data-ttu-id="d8c05-151">이 열에 사용할 종결자 시퀀스의 길이(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-151">Is the length, in bytes, of the terminator sequence to be used for this column.</span></span> <span data-ttu-id="d8c05-152">종결자가 없거나 데이터에 필요하지 않은 경우 이 값을 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-152">If no terminator is present or desired in the data, set this value to 0.</span></span>  
  
 <span data-ttu-id="d8c05-153">*idxServerCol*</span><span class="sxs-lookup"><span data-stu-id="d8c05-153">*idxServerCol*</span></span>  
 <span data-ttu-id="d8c05-154">데이터베이스 테이블에서 열의 서수 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-154">Is the ordinal position of the column in the database table.</span></span> <span data-ttu-id="d8c05-155">첫 번째 열 번호는 1입니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-155">The first column number is 1.</span></span> <span data-ttu-id="d8c05-156">열의 서수 위치는 [SQLColumns](../native-client-odbc-api/sqlcolumns.md)를 사용하여 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-156">The ordinal position of a column is reported by [SQLColumns](../native-client-odbc-api/sqlcolumns.md).</span></span>  
  
 <span data-ttu-id="d8c05-157">이 값이 0이면 대량 복사에서 데이터 파일의 열을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-157">If this value is 0, bulk copy ignores the column in the data file.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="d8c05-158">반환</span><span class="sxs-lookup"><span data-stu-id="d8c05-158">Returns</span></span>  
 <span data-ttu-id="d8c05-159">SUCCEED 또는 FAIL</span><span class="sxs-lookup"><span data-stu-id="d8c05-159">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8c05-160">설명</span><span class="sxs-lookup"><span data-stu-id="d8c05-160">Remarks</span></span>  
 <span data-ttu-id="d8c05-161">**bcp_colfmt** 함수를 사용하여 대량 복사에 사용할 사용자 파일 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-161">The **bcp_colfmt** function allows you to specify the user-file format for bulk copies.</span></span> <span data-ttu-id="d8c05-162">대량 복사의 경우 형식에는 다음과 같은 부분이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-162">For bulk copy, a format contains the following parts:</span></span>  
  
-   <span data-ttu-id="d8c05-163">사용자 파일 열에서 데이터베이스 열로의 매핑</span><span class="sxs-lookup"><span data-stu-id="d8c05-163">A mapping from user-file columns to database columns.</span></span>  
  
-   <span data-ttu-id="d8c05-164">각 사용자 파일 열의 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="d8c05-164">The data type of each user-file column.</span></span>  
  
-   <span data-ttu-id="d8c05-165">각 열에 대한 표시기(옵션)의 길이</span><span class="sxs-lookup"><span data-stu-id="d8c05-165">The length of the optional indicator for each column.</span></span>  
  
-   <span data-ttu-id="d8c05-166">사용자 파일 열당 최대 데이터 길이</span><span class="sxs-lookup"><span data-stu-id="d8c05-166">The maximum length of data per user-file column.</span></span>  
  
-   <span data-ttu-id="d8c05-167">각 열에 대한 종결 바이트 시퀀스(옵션)</span><span class="sxs-lookup"><span data-stu-id="d8c05-167">The optional terminating byte sequence for each column.</span></span>  
  
-   <span data-ttu-id="d8c05-168">선택 사항인 종결 바이트 시퀀스의 길이</span><span class="sxs-lookup"><span data-stu-id="d8c05-168">The length of the optional terminating byte sequence.</span></span>  
  
 <span data-ttu-id="d8c05-169">**bcp_colfmt** 에 대한 각 호출에서는 사용자 파일의 한 열에 대한 서식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-169">Each call to **bcp_colfmt** specifies the format for one user-file column.</span></span> <span data-ttu-id="d8c05-170">예를 들어 다섯 개의 열로 구성된 사용자 데이터 파일의 세 열에 대해 기본 설정을 변경하려면 먼저 [bcp_columns](bcp-columns.md)**(5)** 를 호출한 다음 **bcp_colfmt** 를 다섯 번 호출합니다. 이 중 세 번의 호출에서 사용자 지정 형식을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-170">For example, to change the default settings for three columns in a five-column user data file, first call [bcp_columns](bcp-columns.md)**(5)**, and then call **bcp_colfmt** five times, with three of those calls setting your custom format.</span></span> <span data-ttu-id="d8c05-171">나머지 두 번의 호출에서는 *eUserDataType* 을 0으로 설정하고 *cbIndicator*, *cbUserData*및 *cbUserDataTerm* 을 각각 0, SQL_VARLEN_DATA 및 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-171">For the remaining two calls, set *eUserDataType* to 0, and set *cbIndicator*, *cbUserData*, and *cbUserDataTerm* to 0, SQL_VARLEN_DATA, and 0 respectively.</span></span> <span data-ttu-id="d8c05-172">이 프로시저는 다섯 개의 열을 모두 복사하는데 이 중 세 개는 사용자 지정된 형식으로, 두 개는 기본 형식으로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-172">This procedure copies all five columns, three with your customized format and two with the default format.</span></span>  
  
 <span data-ttu-id="d8c05-173">*cbIndicator*의 경우 이제 큰 값 형식을 나타내는 값 8이 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-173">For *cbIndicator*, a value of 8 to indicate a large value type is now valid.</span></span> <span data-ttu-id="d8c05-174">해당 열이 새로운 최대 유형인 필드에 접두사가 지정되어 있으면 필드 값을 8로만 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-174">If the prefix is specified for a field whose corresponding column is a new max type, it can only be set to 8.</span></span> <span data-ttu-id="d8c05-175">자세한 내용은 [bcp_bind](bcp-bind.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d8c05-175">For details, see [bcp_bind](bcp-bind.md).</span></span>  
  
 <span data-ttu-id="d8c05-176">**bcp_colfmt** 를 호출하기 전에 **bcp_columns**함수를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-176">The **bcp_columns** function must be called before any calls to **bcp_colfmt**.</span></span>  
  
 <span data-ttu-id="d8c05-177">사용자 파일의 각 열에 대해 **bcp_colfmt** 를 한 번씩 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-177">You must call **bcp_colfmt** once for each column in the user file.</span></span>  
  
 <span data-ttu-id="d8c05-178">사용자 파일 열에 대해 **bcp_colfmt** 를 두 번 이상 호출 하면 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-178">Calling **bcp_colfmt** more than once for any user-file column causes an error.</span></span>  
  
 <span data-ttu-id="d8c05-179">사용자 파일의 모든 데이터를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블로 복사할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-179">You do not need to copy all data in a user file to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="d8c05-180">열을 건너뛰려면 *idxServerCol* 매개 변수를 0으로 설정하여 해당 열의 데이터 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-180">To skip a column, specify the format of the data for the column, setting the *idxServerCol* parameter to 0.</span></span> <span data-ttu-id="d8c05-181">열을 건너뛰려면 열 형식을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-181">If you want to skip a column, you must specify its type.</span></span>  
  
 <span data-ttu-id="d8c05-182">[bcp_writefmt](bcp-writefmt.md) 함수는 형식 사양을 유지하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8c05-182">The [bcp_writefmt](bcp-writefmt.md) function can be used to persist the format specification.</span></span>  
  
## <a name="bcp_colfmt-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="d8c05-183">향상된 날짜 및 시간 기능에 대한 bcp_colfmt 지원</span><span class="sxs-lookup"><span data-stu-id="d8c05-183">bcp_colfmt Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="d8c05-184">에서에 대 한 자세한 내용은 날짜/시간 형식에 대 한 *Euserdatatype* 매개 변수와 함께 사용 되는 형식에 대 한 [대량 복사 변경&#41;OLE DB &#40;내용 ](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d8c05-184">For information aboutt he types used with the *eUserDataType* parameter for date/time types, see [Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).</span></span>  
  
 <span data-ttu-id="d8c05-185">자세한 내용은 [ODBC&#41;&#40;날짜 및 시간 향상 ](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d8c05-185">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8c05-186">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d8c05-186">See Also</span></span>  
 [<span data-ttu-id="d8c05-187">Bulk Copy Functions</span><span class="sxs-lookup"><span data-stu-id="d8c05-187">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

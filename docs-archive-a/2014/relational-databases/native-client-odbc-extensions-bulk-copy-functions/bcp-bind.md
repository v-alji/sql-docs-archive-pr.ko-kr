---
title: bcp_bind | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_bind
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_bind function
ms.assetid: 6e335a5c-64b2-4bcf-a88f-35dc9393f329
author: rothja
ms.author: jroth
ms.openlocfilehash: db0a58398bf47bd0bb96bd1ef587d41890ed8461
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730652"
---
# <a name="bcp_bind"></a><span data-ttu-id="7952e-102">bcp_bind</span><span class="sxs-lookup"><span data-stu-id="7952e-102">bcp_bind</span></span>
  <span data-ttu-id="7952e-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 대량 복사를 수행하기 위해 프로그램 변수에서 테이블 열로 데이터를 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-103">Binds data from a program variable to a table column for bulk copy into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7952e-104">구문</span><span class="sxs-lookup"><span data-stu-id="7952e-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_bind (  
HDBC   
hdbc  
,   
LPCBYTE   
pData  
,  
INT   
cbIndicator  
,  
DBINT   
cbData  
,  
LPCBYTE   
pTerm  
,  
INT   
cbTerm  
,  
INT   
eDataType  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="7952e-105">인수</span><span class="sxs-lookup"><span data-stu-id="7952e-105">Arguments</span></span>  
 <span data-ttu-id="7952e-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="7952e-106">*hdbc*</span></span>  
 <span data-ttu-id="7952e-107">대량 복사가 가능한 ODBC 연결 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="7952e-108">*pData*</span><span class="sxs-lookup"><span data-stu-id="7952e-108">*pData*</span></span>  
 <span data-ttu-id="7952e-109">복사 대상 데이터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-109">Is a pointer to the data copied.</span></span> <span data-ttu-id="7952e-110">*Edatatype* 이 sqltext, SQLTEXT, SQLXML, sqltext, SQLTEXT, sqltext, SQLTEXT, SQLBINARY, sqltext 또는 SQLIMAGE, *.pdata* 가 NULL 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-110">If *eDataType* is SQLTEXT, SQLNTEXT, SQLXML, SQLUDT, SQLCHARACTER, SQLVARCHAR, SQLVARBINARY, SQLBINARY, SQLNCHAR or SQLIMAGE, *pData* can be NULL.</span></span> <span data-ttu-id="7952e-111">NULL *.pdata* 는 긴 데이터 값이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [bcp_moretext](bcp-moretext.md)를 사용 하 여 청크로 전송 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-111">A NULL *pData* indicates that long data values will be sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in chunks using [bcp_moretext](bcp-moretext.md).</span></span> <span data-ttu-id="7952e-112">사용자가 바인딩된 필드에 해당 하는 열이 BLOB 열인 경우에는 사용자가 *.pdata* 만 NULL로 설정 해야 합니다. 그렇지 않으면 **bcp_bind** 이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-112">The user should only set *pData* to NULL if the column corresponding to the user bound field is a BLOB column otherwise **bcp_bind** will fail.</span></span>  
  
 <span data-ttu-id="7952e-113">데이터에 표시자가 있으면 이는 메모리에서 데이터 바로 앞에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-113">If indicators are present in the data, they appear in memory directly before the data.</span></span> <span data-ttu-id="7952e-114">*.Pdata* 매개 변수는이 경우 표시기 변수를 가리키며 표시기의 너비 인 *cbindicator* 매개 변수는 대량 복사에서 사용자 데이터를 올바르게 처리 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-114">The *pData* parameter points to the indicator variable in this case, and the width of the indicator, the *cbIndicator* parameter, is used by bulk copy to address user data correctly.</span></span>  
  
 <span data-ttu-id="7952e-115">*cbIndicator*</span><span class="sxs-lookup"><span data-stu-id="7952e-115">*cbIndicator*</span></span>  
 <span data-ttu-id="7952e-116">열 데이터의 길이 또는 Null 표시자의 바이트 단위 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-116">Is the length, in bytes, of a length or null indicator for the column's data.</span></span> <span data-ttu-id="7952e-117">올바른 표시기 길이 값은 0(표시기를 사용하지 않을 경우), 1, 2, 4 또는 8입니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-117">Valid indicator length values are 0 (when using no indicator), 1, 2, 4, or 8.</span></span> <span data-ttu-id="7952e-118">표시자는 메모리에서 데이터 바로 앞에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-118">Indicators appear in memory directly before any data.</span></span> <span data-ttu-id="7952e-119">예를 들어 대량 복사를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에 정수 값을 삽입하기 위해 다음 구조 형식 정의를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-119">For example, the following structure type definition could be used to insert integer values into an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table using bulk copy:</span></span>  
  
```  
typedef struct tagBCPBOUNDINT  
    {  
    int iIndicator;  
    int Value;  
    } BCPBOUNDINT;  
```  
  
 <span data-ttu-id="7952e-120">예제 사례에서 *.pdata* 매개 변수는 구조체의 선언 된 인스턴스 주소 (BCPBOUNDINT *iindicator* 구조체 멤버의 주소)로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-120">In the example case, the *pData* parameter would be set to the address of a declared instance of the structure, the address of the BCPBOUNDINT *iIndicator* structure member.</span></span> <span data-ttu-id="7952e-121">*Cbindicator* 매개 변수는 정수 크기 (sizeof (int))로 설정 되 고, *cbindicator* 매개 변수는 다시 정수 크기 (sizeof (int))로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-121">The *cbIndicator* parameter would be set to the size of an integer (sizeof(int)), and the *cbData* parameter would again be set to the size of an integer (sizeof(int)).</span></span> <span data-ttu-id="7952e-122">바인딩된 열에 대해 NULL 값을 포함 하는 서버에 행을 대량 복사 하려면 인스턴스의 *Iindicator* 멤버 값을 SQL_NULL_DATA으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-122">To bulk copy a row to the server containing a NULL value for the bound column, the value of the instance's *iIndicator* member should be set to SQL_NULL_DATA.</span></span>  
  
 <span data-ttu-id="7952e-123">*cbData*</span><span class="sxs-lookup"><span data-stu-id="7952e-123">*cbData*</span></span>  
 <span data-ttu-id="7952e-124">프로그램 변수 데이터에서 길이 또는 Null 표시자나 종결자의 길이를 제외한 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-124">Is the count of bytes of data in the program variable, not including the length of any length or null indicator or terminator.</span></span>  
  
 <span data-ttu-id="7952e-125">*Cbdata* 를 SQL_NULL_DATA로 설정 하면 서버에 복사 된 모든 행에는 열에 대 한 NULL 값이 포함 되어 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-125">Setting *cbData* to SQL_NULL_DATA signifies that all rows copied to the server contain a NULL value for the column.</span></span>  
  
 <span data-ttu-id="7952e-126">*Cbdata* 를 SQL_VARLEN_DATA로 설정 하면 시스템에서 문자열 종결자 또는 다른 메서드를 사용 하 여 복사 되는 데이터의 길이를 결정 하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-126">Setting *cbData* to SQL_VARLEN_DATA indicates that the system will use a string terminator, or other method, to determine the length of data copied.</span></span>  
  
 <span data-ttu-id="7952e-127">정수와 같은 고정 길이 데이터 형식의 경우 시스템은 데이터 형식으로 데이터의 길이를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-127">For fixed-length data types, such as integers, the data type indicates the length of the data to the system.</span></span> <span data-ttu-id="7952e-128">따라서 고정 길이 데이터 형식의 경우 *Cbdata* 를 안전 하 게 SQL_VARLEN_DATA 하거나 데이터 길이에 안전 하 게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-128">Therefore, for fixed-length data types, *cbData* can safely be SQL_VARLEN_DATA or the length of the data.</span></span>  
  
 <span data-ttu-id="7952e-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]문자 및 이진 데이터 형식의 경우 *cbdata* 는 SQL_VARLEN_DATA, SQL_NULL_DATA, 양수 값 또는 0 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-129">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character and binary data types, *cbData* can be SQL_VARLEN_DATA, SQL_NULL_DATA, some positive value, or 0.</span></span> <span data-ttu-id="7952e-130">*Cbdata* 가 SQL_VARLEN_DATA 되 면 시스템에서는 길이/null 표시기 (있는 경우) 또는 종결자 시퀀스를 사용 하 여 데이터 길이를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-130">If *cbData* is SQL_VARLEN_DATA, the system uses either a length/null indicator (if present) or a terminator sequence to determine the length of the data.</span></span> <span data-ttu-id="7952e-131">두 가지가 모두 제공되면 시스템은 복사할 데이터가 적은 항목을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-131">If both are supplied, the system uses the one that results in the least amount of data being copied.</span></span> <span data-ttu-id="7952e-132">*Cbdata* 가 SQL_VARLEN_DATA 경우 열의 데이터 형식이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 문자 또는 이진 형식이 며 길이 표시기와 종결자 시퀀스를 모두 지정 하지 않으면 시스템에서 오류 메시지를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-132">If *cbData* is SQL_VARLEN_DATA, the data type of the column is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character or binary type, and neither a length indicator nor a terminator sequence is specified, the system returns an error message.</span></span>  
  
 <span data-ttu-id="7952e-133">*Cbdata* 가 0 이거나 양수 값 이면 시스템은 *cbdata* 를 데이터 길이로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-133">If *cbData* is 0 or a positive value, the system uses *cbData* as the data length.</span></span> <span data-ttu-id="7952e-134">그러나 *cbdata* 값이 양수이 고 길이 표시자 또는 종결자 시퀀스가 제공 된 경우 시스템은 복사 되는 데이터의 양이 가장 적은 메서드를 사용 하 여 데이터 길이를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-134">However, if, in addition to a positive *cbData* value, a length indicator or terminator sequence is provided, the system determines the data length by using the method that results in the least amount of data being copied.</span></span>  
  
 <span data-ttu-id="7952e-135">*Cbdata* 매개 변수 값은 데이터의 바이트 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-135">The *cbData* parameter value represents the count of bytes of data.</span></span> <span data-ttu-id="7952e-136">문자 데이터가 유니코드 와이드 문자로 표현 되는 경우 양의 *Cbdata* 매개 변수 값은 문자 수와 각 문자의 바이트 크기를 곱한 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-136">If character data is represented by Unicode wide characters, then a positive *cbData* parameter value represents the number of characters multiplied by the size in bytes of each character.</span></span>  
  
 <span data-ttu-id="7952e-137">*pTerm*</span><span class="sxs-lookup"><span data-stu-id="7952e-137">*pTerm*</span></span>  
 <span data-ttu-id="7952e-138">바이트 패턴에 대한 포인터이며 있는 경우 이 프로그램 변수의 끝을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-138">Is a pointer to the byte pattern, if any, that marks the end of this program variable.</span></span> <span data-ttu-id="7952e-139">예를 들어 ANSI 및 MBCS C 문자열은 일반적으로 1바이트 종결자(\0)를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-139">For example, ANSI and MBCS C strings usually have a 1-byte terminator (\0).</span></span>  
  
 <span data-ttu-id="7952e-140">변수에 종결자가 없는 경우 *Pterm* 을 NULL로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-140">If there is no terminator for the variable, set *pTerm* to NULL.</span></span>  
  
 <span data-ttu-id="7952e-141">C Null 종결자를 프로그램 변수 종결자로 지정하기 위해 빈 문자열("")을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-141">You can use an empty string ("") to designate the C null terminator as the program-variable terminator.</span></span> <span data-ttu-id="7952e-142">Null로 끝나는 빈 문자열은 단일 바이트 (종결자 바이트 자체)를 구성 하므로 *Cbterm* 을 1로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-142">Because the null-terminated empty string constitutes a single byte (the terminator byte itself), set *cbTerm* to 1.</span></span> <span data-ttu-id="7952e-143">예를 들어 *szName* 의 문자열이 null로 종료 되 고 해당 종결자를 사용 하 여 길이를 나타내야 함을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-143">For example, to indicate that the string in *szName* is null-terminated and that the terminator should be used to indicate the length:</span></span>  
  
```  
bcp_bind(hdbc, szName, 0,  
   SQL_VARLEN_DATA, "", 1,  
   SQLCHARACTER, 2)  
```  
  
 <span data-ttu-id="7952e-144">이 예제의 종료 되지 않은 형식은 15 자를 *szName* 변수에서 바인딩된 테이블의 두 번째 열로 복사 했음을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-144">A nonterminated form of this example could indicate that 15 characters be copied from the *szName* variable to the second column of the bound table:</span></span>  
  
```  
bcp_bind(hdbc, szName, 0, 15,   
   NULL, 0, SQLCHARACTER, 2)  
```  
  
 <span data-ttu-id="7952e-145">대량 복사 API는 필요한 경우 유니코드에서 MBCS로의 문자 변환을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-145">The bulk copy API performs Unicode-to-MBCS character conversion as required.</span></span> <span data-ttu-id="7952e-146">종결자 바이트 문자열 및 바이트 문자열 길이를 모두 올바르게 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-146">Make sure that both the terminator byte string and the length of the byte string are set correctly.</span></span> <span data-ttu-id="7952e-147">예를 들어 *szName* 의 문자열이 유니코드 null 종결자 값으로 종료 된 유니코드 와이드 문자열 임을 나타내려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-147">For example, to indicate that the string in *szName* is a Unicode wide character string, terminated by the Unicode null terminator value:</span></span>  
  
```  
bcp_bind(hdbc, szName, 0,   
   SQL_VARLEN_DATA, L"",  
   sizeof(WCHAR), SQLNCHAR, 2)  
```  
  
 <span data-ttu-id="7952e-148">바인딩된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 열이 와이드 문자 이면 [bcp_sendrow](bcp-sendrow.md)에서 변환이 수행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-148">If the bound [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] column is wide character, no conversion is performed on [bcp_sendrow](bcp-sendrow.md).</span></span> <span data-ttu-id="7952e-149">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 열이 MBCS 문자 형식이면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 데이터를 보내는 동안 와이드 문자가 멀티바이트 문자로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-149">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] column is an MBCS character type, wide character to multibyte character conversion is performed as the data is sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="7952e-150">*cbTerm*</span><span class="sxs-lookup"><span data-stu-id="7952e-150">*cbTerm*</span></span>  
 <span data-ttu-id="7952e-151">프로그램 변수에 종결자가 있는 경우 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-151">Is the count of bytes present in the terminator for the program variable, if any.</span></span> <span data-ttu-id="7952e-152">변수에 종결자가 없는 경우 *Cbterm* 을 0으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-152">If there is no terminator for the variable, set *cbTerm* to 0.</span></span>  
  
 <span data-ttu-id="7952e-153">*eDataType*</span><span class="sxs-lookup"><span data-stu-id="7952e-153">*eDataType*</span></span>  
 <span data-ttu-id="7952e-154">프로그램 변수의 C 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-154">Is the C data type of the program variable.</span></span> <span data-ttu-id="7952e-155">프로그램 변수의 데이터는 데이터베이스 열의 형식으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-155">The data in the program variable is converted to the type of the database column.</span></span> <span data-ttu-id="7952e-156">이 매개 변수가 0이면 변환이 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-156">If this parameter is 0, no conversion is performed.</span></span>  
  
 <span data-ttu-id="7952e-157">*Edatatype* 매개 변수는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC C 데이터 형식 열거자가 아닌 sqlncli의 데이터 형식 토큰에 의해 열거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-157">The *eDataType* parameter is enumerated by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type tokens in sqlncli.h, not the ODBC C data type enumerators.</span></span> <span data-ttu-id="7952e-158">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 특정 형식 SQLINT2를 사용하여 2바이트 정수인 ODBC 형식 SQL_C_SHORT를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-158">For example, you can specify a two-byte integer, ODBC type SQL_C_SHORT, using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific type SQLINT2.</span></span>  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<span data-ttu-id="7952e-159">는 paramenter에 SQLXML 및 SQLUDT 데이터 형식 토큰에 대 한 지원을 도입 *`eDataType`* 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-159">introduced support for SQLXML and SQLUDT data type tokens in the *`eDataType`* paramenter.</span></span>  
  
 <span data-ttu-id="7952e-160">*idxServerCol*</span><span class="sxs-lookup"><span data-stu-id="7952e-160">*idxServerCol*</span></span>  
 <span data-ttu-id="7952e-161">데이터 복사 대상인 데이터베이스 테이블 열의 서수 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-161">Is the ordinal position of the column in the database table to which the data is copied.</span></span> <span data-ttu-id="7952e-162">테이블의 첫 번째 열은 열 1입니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-162">The first column in a table is column 1.</span></span> <span data-ttu-id="7952e-163">열의 서수 위치는 [SQLColumns](../native-client-odbc-api/sqlcolumns.md)를 사용하여 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-163">The ordinal position of a column is reported by [SQLColumns](../native-client-odbc-api/sqlcolumns.md).</span></span>  
  
## <a name="returns"></a><span data-ttu-id="7952e-164">반환</span><span class="sxs-lookup"><span data-stu-id="7952e-164">Returns</span></span>  
 <span data-ttu-id="7952e-165">SUCCEED 또는 FAIL</span><span class="sxs-lookup"><span data-stu-id="7952e-165">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7952e-166">설명</span><span class="sxs-lookup"><span data-stu-id="7952e-166">Remarks</span></span>  
 <span data-ttu-id="7952e-167">**Bcp_bind** 를 사용 하 여 프로그램 변수에서의 테이블로 데이터를 빠르고 효율적으로 복사할 수 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-167">Use **bcp_bind** for a fast, efficient way to copy data from a program variable into a table in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="7952e-168">이 또는 다른 대량 복사 함수를 호출 하기 전에 [bcp_init](bcp-init.md) 를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-168">Call [bcp_init](bcp-init.md) before calling this or any other bulk-copy function.</span></span> <span data-ttu-id="7952e-169">**Bcp_init** 를 호출 하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 대상 테이블이 대량 복사로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-169">Calling **bcp_init** sets the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] target table for bulk copy.</span></span> <span data-ttu-id="7952e-170">**Bcp_bind** 및 [bcp_sendrow](bcp-sendrow.md)와 함께 사용 하기 위해 **bcp_init** 를 호출 하는 경우 데이터 파일을 나타내는 **bcp_init** _szdatafile_ 파일 매개 변수가 NULL로 설정 됩니다. **bcp_init**_edirection_ 매개 변수는 DB_IN로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-170">When calling **bcp_init** for use with **bcp_bind** and [bcp_sendrow](bcp-sendrow.md), the **bcp_init** _szDataFile_ parameter, indicating the data file, is set to NULL; the **bcp_init**_eDirection_ parameter is set to DB_IN.</span></span>  
  
 <span data-ttu-id="7952e-171">복사할 테이블의 모든 열에 대해 별도의 **bcp_bind** 호출을 수행 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-171">Make a separate **bcp_bind** call for every column in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table into which you want to copy.</span></span> <span data-ttu-id="7952e-172">필요한 **bcp_bind** 호출이 완료 되 면 **bcp_sendrow** 를 호출 하 여 프로그램 변수의 데이터 행을로 보냅니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="7952e-172">After the necessary **bcp_bind** calls have been made, then call **bcp_sendrow** to send a row of data from your program variables to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7952e-173">열을 다시 바인딩하는 것은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-173">Rebinding a column is not supported.</span></span>  
  
 <span data-ttu-id="7952e-174">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]이미 받은 행을 커밋할 때마다 [bcp_batch](bcp-batch.md)를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-174">Whenever you want [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to commit the rows already received, call [bcp_batch](bcp-batch.md).</span></span> <span data-ttu-id="7952e-175">예를 들어 1000 행이 삽입 될 때마다 또는 다른 간격으로 **bcp_batch** 를 한 번씩 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-175">For example, call **bcp_batch** once for every 1000 rows inserted or at any other interval.</span></span>  
  
 <span data-ttu-id="7952e-176">삽입할 행이 더 이상 없는 경우 [bcp_done](bcp-done.md)를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-176">When there are no more rows to be inserted, call [bcp_done](bcp-done.md).</span></span> <span data-ttu-id="7952e-177">그렇게 하지 않으면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-177">Failure to do so results in an error.</span></span>  
  
 <span data-ttu-id="7952e-178">[Bcp_control](bcp-control.md)로 지정 된 컨트롤 매개 변수 설정은 **bcp_bind** 행 전송에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-178">Control parameter settings, specified with [bcp_control](bcp-control.md), have no effect on **bcp_bind** row transfers.</span></span>  
  
 <span data-ttu-id="7952e-179">열에 대 한 .Pdata가 [bcp_moretext](bcp-moretext.md)에 대 한 호출에서 제공 되기 때문에 열에 대해 *.pdata* 가 null로 설정 된 경우 *edatatype* 이 SQLTEXT, SQLTEXT, SQLXML, SQLTEXT, SQLTEXT, SQLTEXT, SQLTEXT, SQLBINARY, sqltext 또는 SQLIMAGE로 설정 된 모든 후속 열도 null로 설정 된 *.pdata* 에 바인딩되어야 하 고를 호출 하 여 해당 값을 제공 해야 `bcp_moretext`</span><span class="sxs-lookup"><span data-stu-id="7952e-179">If *pData* for a column is set to NULL because its value will be supplied by calls to [bcp_moretext](bcp-moretext.md), any subsequent columns with *eDataType* set to SQLTEXT, SQLNTEXT, SQLXML, SQLUDT, SQLCHARACTER, SQLVARCHAR, SQLVARBINARY, SQLBINARY, SQLNCHAR, or SQLIMAGE must also be bound with *pData* set to NULL, and their values must also be supplied by calls to `bcp_moretext`.</span></span>  
  
 <span data-ttu-id="7952e-180">, 또는와 같은 새로운 대량 값 형식의 `varchar(max)` 경우 `varbinary(max)` `nvarchar(max)` *edatatype* 매개 변수에서 sqlcharacter, SQLCHARACTER, SQLCHARACTER, SQLBINARY 및 sqlcharacter를 형식 표시기로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-180">For new large value types, such as `varchar(max)`, `varbinary(max)`, or `nvarchar(max)`, you can use SQLCHARACTER, SQLVARCHAR, SQLVARBINARY, SQLBINARY, and SQLNCHAR as type indicators in the *eDataType* parameter.</span></span>  
  
 <span data-ttu-id="7952e-181">*Cbterm* 이 0이 아니면 접두사 (*cbterm*)에 대 한 값 (1, 2, 4 또는 8)이 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-181">If *cbTerm* is not 0, any value (1, 2, 4, or 8) is valid for the prefix (*cbIndicator*).</span></span> <span data-ttu-id="7952e-182">이 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client는 종결자를 검색 하 고, 종결자 (*i*)와 관련 된 데이터 길이를 계산 하 고, *cbdata* 를 i의 작은 값과 접두사 값으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-182">In this situation, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client will search for the terminator, calculate data length with respect to the terminator (*i*), and set the *cbData* to the smaller value of i and the value of prefix.</span></span>  
  
 <span data-ttu-id="7952e-183">*Cbterm* 이 0이 고 *cbterm* (접두사)가 0이 아니면 *cbterm* 8 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-183">If *cbTerm* is 0 and *cbIndicator* (the prefix) is not 0, *cbIndicator* must be 8.</span></span> <span data-ttu-id="7952e-184">8바이트 접두사는 다음과 같은 값을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-184">The 8 byte prefix can take the following values:</span></span>  
  
-   <span data-ttu-id="7952e-185">0xFFFFFFFFFFFFFFFF는 필드의 Null 값을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-185">0xFFFFFFFFFFFFFFFF means a null value for the field</span></span>  
  
-   <span data-ttu-id="7952e-186">0xFFFFFFFFFFFFFFFE는 청크의 데이터를 효과적으로 서버에 보내는 데 사용할 수 있는 특수한 접두사 값입니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-186">0xFFFFFFFFFFFFFFFE is treated as a special prefix value which is used for efficiently sending data in chunks to the server.</span></span> <span data-ttu-id="7952e-187">이 특수한 접두사를 사용한 데이터의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-187">The format of data with this special prefix is:</span></span>  
  
-   <span data-ttu-id="7952e-188"><SPECIAL_PREFIX> \<0 or more  DATA CHUNKS> <ZERO_CHUNK> 위치:</span><span class="sxs-lookup"><span data-stu-id="7952e-188"><SPECIAL_PREFIX> \<0 or more  DATA CHUNKS> <ZERO_CHUNK> where:</span></span>  
  
-   <span data-ttu-id="7952e-189">SPECIAL_PREFIX는 0xFFFFFFFFFFFFFFFE입니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-189">SPECIAL_PREFIX is 0xFFFFFFFFFFFFFFFE</span></span>  
  
-   <span data-ttu-id="7952e-190">DATA_CHUNK는 청크의 길이를 포함하는 4바이트 접두사이며, 이 뒤에는 4바이트 접두사에 길이가 지정된 실제 데이터가 옵니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-190">DATA_CHUNK is a 4 byte prefix containing length of the chunk,followed by the actual data whose length is specified in the 4 byte prefix.</span></span>  
  
-   <span data-ttu-id="7952e-191">ZERO_CHUNK는 데이터의 끝을 나타내는 모든 0(00000000)을 포함하는 4바이트 값입니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-191">ZERO_CHUNK is a 4 byte value containing all zeros (00000000) indicating the end of data.</span></span>  
  
-   <span data-ttu-id="7952e-192">다른 모든 유효한 8바이트 길이는 일반적인 데이터 길이로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-192">Any other valid 8 byte length is treated as a regular data length.</span></span>  
  
 <span data-ttu-id="7952e-193">**Bcp_bind** 를 사용할 때 [bcp_columns](bcp-columns.md) 를 호출 하면 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="7952e-193">Calling [bcp_columns](bcp-columns.md) when using **bcp_bind** results in an error.</span></span>  
  
## <a name="bcp_bind-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="7952e-194">향상된 날짜 및 시간 기능을 위한 bcp_bind 지원</span><span class="sxs-lookup"><span data-stu-id="7952e-194">bcp_bind Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="7952e-195">날짜/시간 형식에 대 한 *Edatatype* 매개 변수와 함께 사용 되는 형식에 대 한 자세한 내용은 [향상 된 날짜 및 시간 형식에 대 한 대량 복사 변경 내용 &#40;OLE DB 및 ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7952e-195">For information about the types used with the *eDataType* parameter for date/time types, see [Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).</span></span>  
  
 <span data-ttu-id="7952e-196">자세한 내용은 [ODBC&#41;&#40;날짜 및 시간 향상 ](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7952e-196">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7952e-197">예제</span><span class="sxs-lookup"><span data-stu-id="7952e-197">Example</span></span>  
  
```  
#include sql.h  
#include sqlext.h  
#include odbcss.h  
// Variables like henv not specified.  
HDBC      hdbc;  
char         szCompanyName[MAXNAME];  
DBINT      idCompany;  
DBINT      nRowsProcessed;  
DBBOOL      bMoreData;  
char*      pTerm = "\t\t";  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source; return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bcp.   
if (bcp_init(hdbc, "comdb..accounts_info", NULL, NULL  
   DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Bind program variables to table columns.   
if (bcp_bind(hdbc, (LPCBYTE) &idCompany, 0, sizeof(DBINT), NULL, 0,  
   SQLINT4, 1)    == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_bind(hdbc, (LPCBYTE) szCompanyName, 0, SQL_VARLEN_DATA,  
   (LPCBYTE) pTerm, strnlen(pTerm, sizeof(pTerm)), SQLCHARACTER, 2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
while (TRUE)  
   {  
   // Retrieve and process program data.   
   if ((bMoreData = getdata(&idCompany, szCompanyName)) == TRUE)  
      {  
      // Send the data.   
      if (bcp_sendrow(hdbc) == FAIL)  
         {  
         // Raise error and return.  
         return;  
         }  
      }  
   else  
      {  
      // Break out of loop.  
      break;  
      }  
   }  
  
// Terminate the bulk copy operation.  
if ((nRowsProcessed = bcp_done(hdbc)) == -1)  
   {  
   printf_s("Bulk-copy unsuccessful.\n");  
   return;  
   }  
  
printf_s("%ld rows copied.\n", nRowsProcessed);  
```  
  
## <a name="see-also"></a><span data-ttu-id="7952e-198">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7952e-198">See Also</span></span>  
 [<span data-ttu-id="7952e-199">Bulk Copy Functions</span><span class="sxs-lookup"><span data-stu-id="7952e-199">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

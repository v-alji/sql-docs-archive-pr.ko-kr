---
title: 데이터 형식 매핑 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- mapping data types [ODBC]
- result sets [ODBC], data types
- ODBC data types, mapping
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- data types [ODBC], mapping
- sql_variant data type
- SQL Server Native Client ODBC driver, data types
ms.assetid: 4ba0924d-9fca-4c48-aced-0a8d817b3dde
author: rothja
ms.author: jroth
ms.openlocfilehash: 545e738afb6b3283b2ff2f3830921da8ed13202f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741975"
---
# <a name="mapping-data-types-odbc"></a><span data-ttu-id="fb40c-102">데이터 형식 매핑(ODBC)</span><span class="sxs-lookup"><span data-stu-id="fb40c-102">Mapping Data Types (ODBC)</span></span>
  <span data-ttu-id="fb40c-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT odbc 드라이버는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sql 데이터 형식을 odbc sql 데이터 형식에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="fb40c-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver maps [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL data types to ODBC SQL data types.</span></span> <span data-ttu-id="fb40c-104">아래 섹션에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL 데이터 형식과 이러한 데이터 형식이 매핑되는 ODBC SQL 데이터 형식에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fb40c-104">The sections below discuss the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL data types and the ODBC SQL data types to which they map.</span></span> <span data-ttu-id="fb40c-105">또한 ODBC SQL 데이터 형식 및 해당 ODBC C 데이터 형식과 지원되는 변환 및 기본 변환에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fb40c-105">They also discuss the ODBC SQL data types and their corresponding ODBC C data types, and the supported and default conversions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb40c-106">Timestamp [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **timestamp** 데이터 형식은 **timestamp** 열의 값이 **datetime** 값이 아니라 행의 작업 순서를 나타내는 **BINARY (8)** 또는 **VARBINARY (8)** 값 이기 때문에 SQL_BINARY 또는 SQL_VARBINARY ODBC 데이터 형식에 매핑됩니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="fb40c-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**timestamp** data type maps to the SQL_BINARY or SQL_VARBINARY ODBC data type because the values in **timestamp** columns are not **datetime** values, but **binary(8)** or **varbinary(8)** values that indicate the sequence of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] activity on the row.</span></span> <span data-ttu-id="fb40c-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버에서 바이트 수가 홀수인 SQL_C_WCHAR(유니코드) 값을 발견하면 후행 홀수 바이트가 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="fb40c-107">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver encounters a SQL_C_WCHAR (Unicode) value that is an odd number of bytes, the trailing odd byte is truncated.</span></span>  
  
## <a name="dealing-with-sql_variant-data-type-in-odbc"></a><span data-ttu-id="fb40c-108">ODBC의 sql_variant 데이터 형식 처리</span><span class="sxs-lookup"><span data-stu-id="fb40c-108">Dealing with sql_variant Data Type in ODBC</span></span>  
 <span data-ttu-id="fb40c-109">**Sql_variant** 데이터 형식 열에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **text**, **ntext**및 **image**와 같은 lob (large objects)를 제외한의 데이터 형식이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb40c-109">The **sql_variant** data type column can contain any of the data types in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] except large objects (LOBs), such as **text**, **ntext**, and **image**.</span></span> <span data-ttu-id="fb40c-110">예를 들어 열에는 일부 행에 대해 **smallint** 값, 다른 행의 경우 **float** 값, 나머지에는 **char/nchar** 값이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb40c-110">For example, the column could contain **smallint** values for some rows, **float** values for other rows, and **char/nchar** values in the remainder.</span></span>  
  
 <span data-ttu-id="fb40c-111">**Sql_variant** 데이터 형식은 Microsoft Visual Basic의 **variant** 데이터 형식과 비슷합니다??.</span><span class="sxs-lookup"><span data-stu-id="fb40c-111">The **sql_variant** data type is similar to the **Variant** data type in Microsoft Visual Basic??.</span></span>  
  
### <a name="retrieving-data-from-the-server"></a><span data-ttu-id="fb40c-112">서버에서 데이터 검색</span><span class="sxs-lookup"><span data-stu-id="fb40c-112">Retrieving Data from the Server</span></span>  
 <span data-ttu-id="fb40c-113">ODBC에는의 ODBC 드라이버를 사용 하 여 **sql_variant** 데이터 형식의 사용을 제한 하는 variant 형식의 개념이 없습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="fb40c-113">ODBC does not have a concept of variant types, limiting the use of the **sql_variant** data type with an ODBC driver in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="fb40c-114">에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 바인딩이 지정 된 경우 **sql_variant** 데이터 형식이 문서화 된 ODBC 데이터 형식 중 하나에 바인딩되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb40c-114">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], if binding is specified, the **sql_variant** data type must be bound to one of the documented ODBC data types.</span></span> <span data-ttu-id="fb40c-115">Native Client ODBC 드라이버와 관련 된 새 특성인 **SQL_CA_SS_VARIANT_TYPE**는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **sql_variant** 열에 있는 인스턴스의 데이터 형식을 사용자에 게 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb40c-115">**SQL_CA_SS_VARIANT_TYPE**, a new attribute specific to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver, returns the data type of an instance in the **sql_variant** column to the user.</span></span>  
  
 <span data-ttu-id="fb40c-116">바인딩이 지정 되지 않은 경우 [SQLGetData](../native-client-odbc-api/sqlgetdata.md) 함수를 사용 하 여 **sql_variant** 열에서 인스턴스의 데이터 형식을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb40c-116">If no binding is specified, the [SQLGetData](../native-client-odbc-api/sqlgetdata.md) function can be used to determine the data type of an instance in the **sql_variant** column.</span></span>  
  
 <span data-ttu-id="fb40c-117">**Sql_variant** 데이터를 검색 하려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb40c-117">To retrieve **sql_variant** data follow these steps.</span></span>  
  
1.  <span data-ttu-id="fb40c-118">**Sqlfetch** 를 호출 하 여 검색 된 행에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb40c-118">Call **SQLFetch** to position to the row retrieved.</span></span>  
  
2.  <span data-ttu-id="fb40c-119">**SQLGetData**를 호출 하 여 형식에 대 한 SQL_C_BINARY를 지정 하 고 데이터 길이에 대해 0을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb40c-119">Call **SQLGetData**, specifying SQL_C_BINARY for the type and 0 for the data length.</span></span> <span data-ttu-id="fb40c-120">이렇게 하면 드라이버가 **sql_variant** 헤더를 강제로 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="fb40c-120">This forces the driver to read the **sql_variant** header.</span></span> <span data-ttu-id="fb40c-121">헤더는 **sql_variant** 열에 해당 인스턴스의 데이터 형식을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb40c-121">The header provides the data type of that instance in the **sql_variant** column.</span></span> <span data-ttu-id="fb40c-122">**SQLGetData** 는 값의 크기 (바이트)를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb40c-122">**SQLGetData** returns the size (in bytes) of the value.</span></span>  
  
3.  <span data-ttu-id="fb40c-123">특성 값으로 **SQL_CA_SS_VARIANT_TYPE** 를 지정 하 여 [sqlcolattribute](../native-client-odbc-api/sqlcolattribute.md) 를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb40c-123">Call [SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) by specifying **SQL_CA_SS_VARIANT_TYPE** as its attribute value.</span></span> <span data-ttu-id="fb40c-124">이 함수는 **sql_variant** 열에 있는 인스턴스의 C 데이터 형식을 클라이언트에 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb40c-124">This function will return the C data type of the instance in the **sql_variant** column to the client.</span></span>  
  
 <span data-ttu-id="fb40c-125">위의 단계를 보여 주는 코드 세그먼트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fb40c-125">Here is a code segment showing the preceding steps.</span></span>  
  
```  
while ((retcode = SQLFetch (hstmt))==SQL_SUCCESS)  
{  
    if (retcode != SQL_SUCCESS && retcode != SQL_SUCCESS_WITH_INFO)  
    {  
        SQLError (NULL, NULL, hstmt, NULL,   
                    &lNativeError,szError,MAX_DATA,&sReturned);  
        printf_s ("%s\n",szError);  
        goto Exit;  
    }  
    retcode = SQLGetData (hstmt, 1, SQL_C_BINARY,   
                                pBuff,0,&Indicator);//Figure out the length  
    if (retcode != SQL_SUCCESS_WITH_INFO && retcode != SQL_SUCCESS)  
    {  
        SQLError (NULL, NULL, hstmt, NULL, &lNativeError,   
                    szError,MAX_DATA,&sReturned);  
        printf_s ("%s\n",szError);  
        goto Exit;  
    }  
    printf_s ("Byte length : %d ",Indicator); //Print out the byte length  
  
    int iValue = 0;  
    retcode = SQLColAttribute (hstmt, 1, SQL_CA_SS_VARIANT_TYPE, NULL,   
                                        NULL,NULL,&iValue);  //Figure out the type  
    printf_s ("Sub type = %d ",iValue);//Print the type, the return is C_type of the column]  
  
// Set up a new binding or do the SQLGetData on that column with   
// the appropriate type  
}  
```  
  
 <span data-ttu-id="fb40c-126">사용자가 [SQLBindCol](../native-client-odbc-api/sqlbindcol.md)를 사용 하 여 바인딩을 만드는 경우 드라이버는 메타 데이터 및 데이터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="fb40c-126">If the user creates the binding using [SQLBindCol](../native-client-odbc-api/sqlbindcol.md), the driver reads the metadata and the data.</span></span> <span data-ttu-id="fb40c-127">그런 다음 데이터를 바인딩에 지정된 적절한 ODBC 형식으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="fb40c-127">The driver then converts the data to the appropriate ODBC type specified in the binding.</span></span>  
  
### <a name="sending-data-to-the-server"></a><span data-ttu-id="fb40c-128">데이터를 서버로 보내기</span><span class="sxs-lookup"><span data-stu-id="fb40c-128">Sending Data to the Server</span></span>  
 <span data-ttu-id="fb40c-129">Native Client ODBC 드라이버와 관련 된 새 데이터 유형인 **SQL_SS_VARIANT**는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **sql_variant** 열로 전송 되는 데이터에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb40c-129">**SQL_SS_VARIANT**, a new data type specific to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver, is used for data sent to an **sql_variant** column.</span></span> <span data-ttu-id="fb40c-130">매개 변수를 사용 하 여 서버에 데이터를 전송 하는 경우 (예: INSERT INTO TableName VALUES (?,?)) [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) 는 C 형식 및 해당 형식을 포함 하는 매개 변수 정보를 지정 하는 데 사용 됩니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="fb40c-130">When sending data to the server using parameters (for example, INSERT INTO TableName VALUES (?,?)), [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) is used to specify the parameter information including the C type and the corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type.</span></span> <span data-ttu-id="fb40c-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 드라이버는 C 데이터 형식을 적절 한 **sql_variant** 하위 형식 중 하나로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb40c-131">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver will convert the C data type to one of the appropriate **sql_variant** subtypes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb40c-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fb40c-132">See Also</span></span>  
 [<span data-ttu-id="fb40c-133">ODBC&#41;&#40;결과 처리</span><span class="sxs-lookup"><span data-stu-id="fb40c-133">Processing Results &#40;ODBC&#41;</span></span>](processing-results-odbc.md)  
  
  

---
title: bcp_collen | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_collen
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_collen function
ms.assetid: faaf1f7a-81f2-4852-a178-56602c33673a
author: rothja
ms.author: jroth
ms.openlocfilehash: 3099e26b0c2cd0d1cfee7578f5b149b812f01765
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742008"
---
# <a name="bcp_collen"></a><span data-ttu-id="5eeff-102">bcp_collen</span><span class="sxs-lookup"><span data-stu-id="5eeff-102">bcp_collen</span></span>
  <span data-ttu-id="5eeff-103">현재 대량 복사에 대한 프로그램 변수의 데이터 길이를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeff-103">Sets the data length in the program variable for the current bulk copy into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5eeff-104">구문</span><span class="sxs-lookup"><span data-stu-id="5eeff-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_collen (  
HDBC   
hdbc  
,  
DBINT   
cbData  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="5eeff-105">인수</span><span class="sxs-lookup"><span data-stu-id="5eeff-105">Arguments</span></span>  
 <span data-ttu-id="5eeff-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="5eeff-106">*hdbc*</span></span>  
 <span data-ttu-id="5eeff-107">대량 복사가 가능한 ODBC 연결 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="5eeff-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="5eeff-108">*cbData*</span><span class="sxs-lookup"><span data-stu-id="5eeff-108">*cbData*</span></span>  
 <span data-ttu-id="5eeff-109">길이 표시기나 종결자의 길이를 제외한 프로그램 변수의 데이터 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="5eeff-109">Is the length of the data in the program variable, not including the length of any length indicator or terminator.</span></span> <span data-ttu-id="5eeff-110">*Cbdata* 를 SQL_NULL_DATA로 설정 하면 서버에 복사 된 모든 행에는 열에 대 한 NULL 값이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eeff-110">Setting *cbData* to SQL_NULL_DATA indicates all rows copied to the server contain a NULL value for the column.</span></span> <span data-ttu-id="5eeff-111">SQL_VARLEN_DATA로 설정하면 복사되는 데이터의 길이를 확인하는 데 문자열 종결자 또는 다른 메서드가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eeff-111">Setting it to SQL_VARLEN_DATA indicates that a string terminator or other method is used to determine the length of data copied.</span></span> <span data-ttu-id="5eeff-112">길이 표시기와 종결자가 모두 있으면 시스템에서는 복사되는 데이터 크기가 더 작은 것이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eeff-112">If both a length indicator and a terminator exist, the system uses whichever one results in less data being copied.</span></span>  
  
 <span data-ttu-id="5eeff-113">*idxServerCol*</span><span class="sxs-lookup"><span data-stu-id="5eeff-113">*idxServerCol*</span></span>  
 <span data-ttu-id="5eeff-114">데이터가 복사되는 대상 테이블 열의 서수 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="5eeff-114">Is the ordinal position of the column in the table to which the data is copied.</span></span> <span data-ttu-id="5eeff-115">첫 번째 열은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="5eeff-115">The first column is 1.</span></span> <span data-ttu-id="5eeff-116">열의 서수 위치는 [SQLColumns](../native-client-odbc-api/sqlcolumns.md)를 사용하여 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eeff-116">The ordinal position of a column is reported by [SQLColumns](../native-client-odbc-api/sqlcolumns.md).</span></span>  
  
## <a name="returns"></a><span data-ttu-id="5eeff-117">반환</span><span class="sxs-lookup"><span data-stu-id="5eeff-117">Returns</span></span>  
 <span data-ttu-id="5eeff-118">SUCCEED 또는 FAIL</span><span class="sxs-lookup"><span data-stu-id="5eeff-118">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5eeff-119">설명</span><span class="sxs-lookup"><span data-stu-id="5eeff-119">Remarks</span></span>  
 <span data-ttu-id="5eeff-120">**Bcp_collen** 함수를 사용 하면 bcp_sendrow를 사용 하 여 데이터를에 복사할 때 특정 열에 대해 프로그램 변수의 데이터 길이를 변경할 수 있습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [bcp_sendrow](bcp-sendrow.md)</span><span class="sxs-lookup"><span data-stu-id="5eeff-120">The **bcp_collen** function allows you to change the data length in the program variable for a particular column when copying data to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with [bcp_sendrow](bcp-sendrow.md).</span></span>  
  
 <span data-ttu-id="5eeff-121">처음에는 [bcp_bind](bcp-bind.md) 를 호출할 때 데이터 길이가 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eeff-121">Initially, the data length is determined when [bcp_bind](bcp-bind.md) is called.</span></span> <span data-ttu-id="5eeff-122">**Bcp_sendrow** 호출 사이에 데이터 길이가 변경 되 고 길이 접두사나 종결자가 사용 되지 않는 경우 **bcp_collen** 를 호출 하 여 길이를 다시 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eeff-122">If the data length changes between calls to **bcp_sendrow** and no length prefix or terminator is being used, you can call **bcp_collen** to reset the length.</span></span> <span data-ttu-id="5eeff-123">**Bcp_sendrow** 에 대 한 다음 호출에서는 **bcp_collen**에 대 한 호출로 설정 된 길이를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeff-123">The next call to **bcp_sendrow** uses the length set by the call to **bcp_collen**.</span></span>  
  
 <span data-ttu-id="5eeff-124">데이터 길이가 수정 하려는 테이블의 각 열에 대해 **bcp_collen** 를 한 번씩 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeff-124">You must call **bcp_collen** once for each column in the table whose data length you want to modify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5eeff-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5eeff-125">See Also</span></span>  
 [<span data-ttu-id="5eeff-126">Bulk Copy Functions</span><span class="sxs-lookup"><span data-stu-id="5eeff-126">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

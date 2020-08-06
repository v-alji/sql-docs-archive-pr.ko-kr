---
title: bcp_sendrow | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_sendrow
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_sendrow function
ms.assetid: ddbdb4bd-ad4e-4bf1-9a75-656aa26ce10a
author: rothja
ms.author: jroth
ms.openlocfilehash: 3d2f55486ba57101ffc7b1903de5d19ac8eaaca2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649043"
---
# <a name="bcp_sendrow"></a><span data-ttu-id="34460-102">bcp_sendrow</span><span class="sxs-lookup"><span data-stu-id="34460-102">bcp_sendrow</span></span>
  <span data-ttu-id="34460-103">프로그램 변수에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 데이터 행을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="34460-103">Sends a row of data from program variables to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34460-104">구문</span><span class="sxs-lookup"><span data-stu-id="34460-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_sendrow (  
    HDBC   
hdbc  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="34460-105">인수</span><span class="sxs-lookup"><span data-stu-id="34460-105">Arguments</span></span>  
 <span data-ttu-id="34460-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="34460-106">*hdbc*</span></span>  
 <span data-ttu-id="34460-107">대량 복사가 가능한 ODBC 연결 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="34460-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="34460-108">반환</span><span class="sxs-lookup"><span data-stu-id="34460-108">Returns</span></span>  
 <span data-ttu-id="34460-109">SUCCEED 또는 FAIL</span><span class="sxs-lookup"><span data-stu-id="34460-109">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34460-110">설명</span><span class="sxs-lookup"><span data-stu-id="34460-110">Remarks</span></span>  
 <span data-ttu-id="34460-111">**Bcp_sendrow** 함수는 프로그램 변수에서 행을 빌드하고로 보냅니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="34460-111">The **bcp_sendrow** function builds a row from program variables and sends it to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="34460-112">**Bcp_sendrow**를 호출 하기 전에 [bcp_bind](bcp-bind.md) 를 호출 하 여 행 데이터가 포함 된 프로그램 변수를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34460-112">Before calling **bcp_sendrow**, you must make calls to [bcp_bind](bcp-bind.md) to specify the program variables containing row data.</span></span>  
  
 <span data-ttu-id="34460-113">Long, 가변 길이 데이터 형식 (예: SQLTEXT의 *Edatatype* 매개 변수 및 Null이 아닌 *.pdata* 매개 변수)을 지정 하 여 **bcp_bind** 를 호출 하는 경우 **bcp_sendrow** 는 다른 데이터 형식에 대해 수행 되는 것과 같은 방법으로 데이터 값을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="34460-113">If **bcp_bind** is called specifying a long, variable-length data type, for example, an *eDataType* parameter of SQLTEXT and a nonNULL *pData* parameter, **bcp_sendrow** sends the entiredata value, just as it does for any other data type.</span></span> <span data-ttu-id="34460-114">그러나 **bcp_bind** 에 NULL *.pdata* 매개 변수가 있는 경우에는 지정 된 데이터가 있는 모든 열이로 전송 되는 즉시 응용 프로그램에 제어를 반환 **bcp_sendrow** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="34460-114">If, however, **bcp_bind** has a NULL *pData* parameter, **bcp_sendrow** returns control to the application immediately after all columns with data specified are sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="34460-115">그런 다음 응용 프로그램은 [bcp_moretext](bcp-moretext.md) 를 반복적으로 호출 하 여 긴 가변 길이 데이터를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 한 번에 청크로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34460-115">The application can then call [bcp_moretext](bcp-moretext.md) repeatedly to send the long, variable-length data to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a chunk at a time.</span></span> <span data-ttu-id="34460-116">자세한 내용은 [bcp_moretext](bcp-moretext.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="34460-116">For more information, see [bcp_moretext](bcp-moretext.md).</span></span>  
  
 <span data-ttu-id="34460-117">**Bcp_sendrow** 를 사용 하 여 프로그램 변수에서 테이블로 행을 대량 복사 하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용자가 [bcp_batch](bcp-batch.md) 또는 [bcp_done](bcp-done.md)를 호출 하는 경우에만 행이 커밋됩니다.</span><span class="sxs-lookup"><span data-stu-id="34460-117">When **bcp_sendrow** is used to bulk copy rows from program variables into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables, rows are committed only when the user calls [bcp_batch](bcp-batch.md) or [bcp_done](bcp-done.md).</span></span> <span data-ttu-id="34460-118">사용자는 *n 개* 행 마다 또는 들어오는 데이터 기간 사이에 소강 상태가이 있는 경우 **bcp_batch** 를 호출 하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34460-118">The user can choose to call **bcp_batch** once every *n* rows or when there is a lull between periods of incoming data.</span></span> <span data-ttu-id="34460-119">**Bcp_batch** 를 호출 하지 않으면 **bcp_done** 를 호출할 때 행이 커밋됩니다.</span><span class="sxs-lookup"><span data-stu-id="34460-119">If **bcp_batch** is never called, the rows are committed when **bcp_done** is called.</span></span>  
  
 <span data-ttu-id="34460-120">에서 시작 하는 대량 복사의 주요 변경 내용에 대 한 자세한 내용은 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [ODBC&#41;&#40;대량 복사 작업 수행 ](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="34460-120">For information about a breaking change in bulk-copying beginning in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], see [Performing Bulk Copy Operations &#40;ODBC&#41;](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34460-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="34460-121">See Also</span></span>  
 [<span data-ttu-id="34460-122">Bulk Copy Functions</span><span class="sxs-lookup"><span data-stu-id="34460-122">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

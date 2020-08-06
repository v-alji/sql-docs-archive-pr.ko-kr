---
title: bcp_batch | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_batch
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_batch function
ms.assetid: 0bda489e-86bc-4a7e-80f6-96047e03f281
author: rothja
ms.author: jroth
ms.openlocfilehash: 24cdf6e2934c2b80a55d8fa1fcc572a976b636ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650934"
---
# <a name="bcp_batch"></a><span data-ttu-id="bdb6e-102">bcp_batch</span><span class="sxs-lookup"><span data-stu-id="bdb6e-102">bcp_batch</span></span>
  <span data-ttu-id="bdb6e-103">이전에 프로그램 변수에서 대량 복사하고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bcp_sendrow [를 사용하여](bcp-sendrow.md)로 보낸 행을 모두 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb6e-103">Commits all rows previously bulk copied from program variables and sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by [bcp_sendrow](bcp-sendrow.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdb6e-104">구문</span><span class="sxs-lookup"><span data-stu-id="bdb6e-104">Syntax</span></span>  
  
```  
  
DBINT bcp_batch (HDBC  
hdbc  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="bdb6e-105">인수</span><span class="sxs-lookup"><span data-stu-id="bdb6e-105">Arguments</span></span>  
 <span data-ttu-id="bdb6e-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="bdb6e-106">*hdbc*</span></span>  
 <span data-ttu-id="bdb6e-107">대량 복사가 가능한 ODBC 연결 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="bdb6e-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="bdb6e-108">반환</span><span class="sxs-lookup"><span data-stu-id="bdb6e-108">Returns</span></span>  
 <span data-ttu-id="bdb6e-109">**bcp_batch**를 마지막으로 호출한 후 저장된 행의 수입니다. 또는 오류가 발생하는 경우 -1입니다.</span><span class="sxs-lookup"><span data-stu-id="bdb6e-109">The number of rows saved after the last call to **bcp_batch**, or -1 in case of error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdb6e-110">설명</span><span class="sxs-lookup"><span data-stu-id="bdb6e-110">Remarks</span></span>  
 <span data-ttu-id="bdb6e-111">대량 복사 일괄 처리에서 트랜잭션을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="bdb6e-111">Bulk copy batches define transactions.</span></span> <span data-ttu-id="bdb6e-112">애플리케이션에서 [bcp_bind](bcp-bind.md) 및 **bcp_sendrow** 를 사용하여 프로그램 변수에서 SQL Server 테이블로 행을 대량 복사할 때 프로그램에서 **bcp_batch** 또는 [bcp_done](bcp-done.md)을 호출할 경우에만 행이 커밋됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdb6e-112">When an application uses [bcp_bind](bcp-bind.md) and **bcp_sendrow** to bulk copy rows from program variables to SQL Server tables, the rows are committed only when the program calls **bcp_batch** or [bcp_done](bcp-done.md).</span></span>  
  
 <span data-ttu-id="bdb6e-113">**bcp_batch** 는 *n* 번째 행마다 한 번씩 호출하거나 원격 계측 애플리케이션에서처럼 들어오는 데이터에 소강 상태가 있는 경우에 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdb6e-113">You can call **bcp_batch** once every *n* rows or when there is a lull in incoming data (as in a telemetry application).</span></span> <span data-ttu-id="bdb6e-114">애플리케이션에서 **bcp_batch** 를 호출하지 않는 경우에는 **bcp_done** 을 호출할 때만 대량 복사된 행이 커밋됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdb6e-114">If an application does not call **bcp_batch** the bulk copied rows are committed only when **bcp_done** is called.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdb6e-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bdb6e-115">See Also</span></span>  
 [<span data-ttu-id="bdb6e-116">Bulk Copy Functions</span><span class="sxs-lookup"><span data-stu-id="bdb6e-116">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

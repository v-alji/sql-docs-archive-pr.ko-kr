---
title: 텍스트 및 이미지 데이터 대량 복사 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], text data
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], image data
- ODBC, bulk copy operations
ms.assetid: 87155bfa-3a73-4158-9d4d-cb7435dac201
author: rothja
ms.author: jroth
ms.openlocfilehash: 9240fd0eb8c32ed39613824ea5a07764e277160c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661091"
---
# <a name="bulk-copying-text-and-image-data"></a><span data-ttu-id="1d2b2-102">텍스트 및 이미지 데이터 대량 복사</span><span class="sxs-lookup"><span data-stu-id="1d2b2-102">Bulk Copying Text and Image Data</span></span>
  <span data-ttu-id="1d2b2-103">대용량 **text**, **ntext**및 **image** 값은 [bcp_moretext](../native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) 함수를 사용 하 여 대량 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d2b2-103">Large **text**, **ntext**, and **image** values are bulk copied using the [bcp_moretext](../native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) function.</span></span> <span data-ttu-id="1d2b2-104">*.Pdata* 포인터가 NULL로 설정 **된 text**, **ntext**또는 **image** 열에 대 한 [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) 코드를 사용 하 여 데이터가 **bcp_moretext**에 제공 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1d2b2-104">You code [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) for the **text**, **ntext**, or **image** column with a *pData* pointer set to NULL indicating the data will be provided with **bcp_moretext**.</span></span> <span data-ttu-id="1d2b2-105">대량 복사 된 각 행에서 각 **text**, **ntext**또는 **image** 열에 대해 제공 되는 정확한 데이터 길이를 지정 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d2b2-105">It is important to specify the exact length of data supplied for each **text**, **ntext**,or **image** column in each bulk-copied row.</span></span> <span data-ttu-id="1d2b2-106">열에 대 한 데이터 길이가 [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)에 지정 된 열 길이와 다른 경우 [bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) 를 사용 하 여 길이를 적절 한 값으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d2b2-106">If the length of the data for a column is different from the column length specified in [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md), use [bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) to set the length to the proper value.</span></span> <span data-ttu-id="1d2b2-107">[Bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) 은 텍스트가 아닌 모든**텍스트**,**ntext**및**이미지가** 아닌 데이터를 모두 보냅니다. 그런 다음 **bcp_moretext** 를 호출 하 여 **text**, **ntext**또는 **image** 데이터를 별도의 단위로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="1d2b2-107">A [bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) sends all the non-**text**, non-**ntext**, and non-**image** data; you then call **bcp_moretext** to send the **text**, **ntext**, or **image** data in separate units.</span></span> <span data-ttu-id="1d2b2-108">대량 복사 함수는 **bcp_moretext** 를 통해 전송 된 데이터의 길이가 최신 **bcp_collen** 나 **bcp_bind**에 지정 된 길이와 일치 하는 경우 현재 **text**, **ntext**또는 **image** 열에 대해 모든 데이터가 전송 되었음을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d2b2-108">Bulk copy functions determine that all data has been sent for the current **text**, **ntext**, or **image** column when the sum of the lengths of data sent through **bcp_moretext** equals the length specified in the latest **bcp_collen** or **bcp_bind**.</span></span>  
  
 <span data-ttu-id="1d2b2-109">**bcp_moretext** 에는 열을 식별 하는 매개 변수가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1d2b2-109">**bcp_moretext** has no parameter to identify a column.</span></span> <span data-ttu-id="1d2b2-110">한 행에 **text**, **ntext**또는 **image** 열이 여러 개 있는 경우 **bcp_moretext** 는 가장 낮은 서 수 번호가 있는 열로 시작 하는 **text**, **ntext**또는 **image** 열에 대해 작동 하며 서 수 번호가 가장 높은 열로 진행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d2b2-110">When there are multiple **text**, **ntext**, or **image** columns in a row, **bcp_moretext** operates on the **text**, **ntext**, or **image** columns starting with the column having the lowest ordinal number and proceeding to the column with the highest ordinal number.</span></span> <span data-ttu-id="1d2b2-111">전송 된 데이터의 길이가 최신 **bcp_collen** **bcp_bind** 또는 현재 열에 대해 지정 된 길이와 같으면 한 열에서 다음 열로 이동 **bcp_moretext** .</span><span class="sxs-lookup"><span data-stu-id="1d2b2-111">**bcp_moretext** goes from one column to the next when the sum of the lengths of data sent equals the length specified in the latest **bcp_collen** or **bcp_bind** for the current column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d2b2-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1d2b2-112">See Also</span></span>  
 [<span data-ttu-id="1d2b2-113">ODBC&#41;&#40;대량 복사 작업 수행</span><span class="sxs-lookup"><span data-stu-id="1d2b2-113">Performing Bulk Copy Operations &#40;ODBC&#41;</span></span>](performing-bulk-copy-operations-odbc.md)  
  
  

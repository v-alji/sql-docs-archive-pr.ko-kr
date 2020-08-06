---
title: 텍스트 및 이미지 열 관리 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- data types [ODBC], mapping
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 7b543556-ff36-4d35-ac08-de96223d92cd
author: rothja
ms.author: jroth
ms.openlocfilehash: e9d7d5b0f48c68e8ac911f5e274c9afdb8cfe17d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741935"
---
# <a name="managing-text-and-image-columns"></a><span data-ttu-id="1d2e2-102">text 및 image 열 관리</span><span class="sxs-lookup"><span data-stu-id="1d2e2-102">Managing Text and Image Columns</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="1d2e2-103">**text**, **ntext**및 **image** 데이터 (long 데이터 라고도 함)는 **char**, **varchar**, **binary**또는 **varbinary** 열에 맞지 않는 데이터 값을 저장할 수 있는 문자 또는 이진 문자열 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="1d2e2-103">**text**, **ntext**, and **image** data (also referred to as long data) are character or binary string data types that can hold data values too large to fit into **char**, **varchar**, **binary**, or **varbinary** columns.</span></span> <span data-ttu-id="1d2e2-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Text** 데이터 형식은 ODBC SQL_LONGVARCHAR 데이터 형식에 매핑됩니다. **ntext** 는 SQL_WLONGVARCHAR;에 매핑됩니다. 및 **이미지가** SQL_LONGVARBINARY에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d2e2-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **text** data type maps to the ODBC SQL_LONGVARCHAR data type; **ntext** maps to SQL_WLONGVARCHAR; and **image** maps to SQL_LONGVARBINARY.</span></span> <span data-ttu-id="1d2e2-105">긴 문서나 큰 비트맵과 같은 일부 데이터 항목은 너무 커서 메모리에 저장하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d2e2-105">Some data items, such as long documents or large bitmaps, may be too large to store reasonably in memory.</span></span> <span data-ttu-id="1d2e2-106">순차 파트에서 긴 데이터를 검색 하기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NATIVE Client ODBC 드라이버를 사용 하면 응용 프로그램에서 [SQLGetData](../native-client-odbc-api/sqlgetdata.md)를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d2e2-106">To retrieve long data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in sequential parts, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver enables an application to call [SQLGetData](../native-client-odbc-api/sqlgetdata.md).</span></span> <span data-ttu-id="1d2e2-107">긴 데이터를 순차적인 부분으로 전송 하기 위해 응용 프로그램은 [Sqlputdata](../native-client-odbc-api/sqlputdata.md)를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d2e2-107">To send long data in sequential parts, the application can call [SQLPutData](../native-client-odbc-api/sqlputdata.md).</span></span> <span data-ttu-id="1d2e2-108">실행 단계에서 데이터가 전송되는 매개 변수를 실행 시 데이터 매개 변수라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d2e2-108">Parameters for which data is sent at execution time are known as data-at-execution parameters.</span></span>  
  
 <span data-ttu-id="1d2e2-109">응용 프로그램은 **Sqlputdata** 또는 **SQLGetData**를 사용 하 여 긴 데이터 뿐만 아니라 모든 유형의 데이터를 작성 하거나 검색할 수 있지만, **문자** 및 **이진** 데이터만 파트에서 전송 하거나 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d2e2-109">An application can actually write or retrieve any type of data (not just long data) with **SQLPutData** or **SQLGetData**, although only **character** and **binary** data can be sent or retrieved in parts.</span></span> <span data-ttu-id="1d2e2-110">그러나 데이터가 단일 버퍼에 맞게 충분히 작은 경우 일반적으로 **Sqlputdata** 또는 **SQLGetData**를 사용할 이유가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1d2e2-110">However, if the data is small enough to fit in a single buffer, there is generally no reason to use **SQLPutData** or **SQLGetData**.</span></span> <span data-ttu-id="1d2e2-111">단일 버퍼를 매개 변수 또는 열에 바인딩하는 것이 훨씬 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="1d2e2-111">It is much easier to bind the single buffer to the parameter or column.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1d2e2-112">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="1d2e2-112">In This Section</span></span>  
  
-   [<span data-ttu-id="1d2e2-113">바인딩된 Text 및 Image 열과 바인딩되지 않은 Text 및 Image 열</span><span class="sxs-lookup"><span data-stu-id="1d2e2-113">Bound vs. Unbound Text and Image Columns</span></span>](bound-vs-unbound-text-and-image-columns.md)  
  
-   [<span data-ttu-id="1d2e2-114">기록되는 수정 및 기록되지 않는 수정</span><span class="sxs-lookup"><span data-stu-id="1d2e2-114">Logged vs. Unlogged Modifications</span></span>](logged-vs-unlogged-modifications.md)  
  
-   [<span data-ttu-id="1d2e2-115">실행 시 데이터 및 text, ntext 또는 image 열</span><span class="sxs-lookup"><span data-stu-id="1d2e2-115">Data-at-Execution and Text, ntext, or Image Columns</span></span>](data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a><span data-ttu-id="1d2e2-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1d2e2-116">See Also</span></span>  
 [<span data-ttu-id="1d2e2-117">SQL Server Native Client &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="1d2e2-117">SQL Server Native Client &#40;ODBC&#41;</span></span>](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  

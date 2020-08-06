---
title: Bound 및 언바운드 텍스트 및 이미지 열 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: ffd3442e-d880-46e9-b848-2365a09a2406
author: rothja
ms.author: jroth
ms.openlocfilehash: 20a91d26ac8c2d1201386cb19bde13b49a3dbada
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741948"
---
# <a name="bound-vs-unbound-text-and-image-columns"></a><span data-ttu-id="3c83c-102">바인딩된 Text 및 Image 열과 바인딩되지 않은 Text 및 Image 열</span><span class="sxs-lookup"><span data-stu-id="3c83c-102">Bound vs. Unbound Text and Image Columns</span></span>
  <span data-ttu-id="3c83c-103">서버 커서를 사용할 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 드라이버는 **sqlfetch** 가 수행 될 때 바인딩되지 않은 **text**, **ntext**또는 **image** 열에 대 한 데이터를 전송 하지 않도록 최적화 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c83c-103">When using server cursors, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver is optimized to not transmit the data for unbound **text**, **ntext**, or **image** columns at the time **SQLFetch** is performed.</span></span> <span data-ttu-id="3c83c-104">**Text**, **ntext**또는 **image** 데이터는 응용 프로그램이 열에 대해 [SQLGetData](../native-client-odbc-api/sqlgetdata.md) 를 발급할 때까지 서버에서 실제로 검색 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c83c-104">The **text**, **ntext**, or **image** data is not actually retrieved from the server until the application issues [SQLGetData](../native-client-odbc-api/sqlgetdata.md) for the column.</span></span>  
  
 <span data-ttu-id="3c83c-105">사용자가 커서에서 위나 아래로 스크롤 하는 동안 **text**, **ntext**또는 **image** 데이터가 표시 되지 않도록 많은 응용 프로그램을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c83c-105">Many applications can be written so that no **text**, **ntext**, or **image** data is displayed while a user is simply scrolling up and down in a cursor.</span></span> <span data-ttu-id="3c83c-106">사용자가 행을 선택 하 여 세부 정보를 가져오는 경우 응용 프로그램은 **SQLGetData** 를 호출 하 여 **text**, **ntext**또는 **image** 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c83c-106">When a user selects a row to get more detail, the application can then call **SQLGetData** to retrieve the **text**, **ntext**, or **image** data.</span></span> <span data-ttu-id="3c83c-107">이렇게 하면 사용자가 선택 하지 않은 행에 대해 **text**, **ntext**또는 **image** 데이터가 전송 되지 않으므로 매우 많은 양의 데이터가 전송 되는 것을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c83c-107">This will prevent transmitting the **text**, **ntext**, or **image** data for any of the rows the user does not select, and can therefore prevent the transmission of very large amounts of data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c83c-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3c83c-108">See Also</span></span>  
 <span data-ttu-id="3c83c-109">[텍스트 및 이미지 열 관리](managing-text-and-image-columns.md) </span><span class="sxs-lookup"><span data-stu-id="3c83c-109">[Managing Text and Image Columns](managing-text-and-image-columns.md) </span></span>  
 [<span data-ttu-id="3c83c-110">커서 동작</span><span class="sxs-lookup"><span data-stu-id="3c83c-110">Cursor Behaviors</span></span>](../native-client-odbc-cursors/cursor-behaviors.md)  
  
  

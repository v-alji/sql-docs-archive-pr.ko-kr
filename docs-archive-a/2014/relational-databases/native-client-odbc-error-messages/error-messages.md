---
title: 오류 메시지 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], types
- ODBC error handling, message types
- errors [ODBC], types
ms.assetid: 46c0c22e-d105-4d5b-bb9d-5694472e8651
author: rothja
ms.author: jroth
ms.openlocfilehash: d004ba320b50896b6f57c5de335d7f7b3d33e87a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738320"
---
# <a name="error-messages"></a><span data-ttu-id="ad088-102">오류 메시지</span><span class="sxs-lookup"><span data-stu-id="ad088-102">Error Messages</span></span>
  <span data-ttu-id="ad088-103">Native Client ODBC 드라이버에서 반환 하는 메시지의 텍스트는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **SQLGetDiagRec**의 *MessageText* 매개 변수에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad088-103">The text of messages returned by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver is placed in the *MessageText* parameter of **SQLGetDiagRec**.</span></span> <span data-ttu-id="ad088-104">오류의 원본은 메시지 헤더에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad088-104">The source of an error is indicated by the header of the message:</span></span>  
  
 <span data-ttu-id="ad088-105">[Microsoft][ODBC Driver Manager]</span><span class="sxs-lookup"><span data-stu-id="ad088-105">[Microsoft][ODBC Driver Manager]</span></span>  
 <span data-ttu-id="ad088-106">이러한 오류는 ODBC 드라이버 관리자에서 발생됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad088-106">These errors are raised by the ODBC Driver Manager.</span></span>  
  
 <span data-ttu-id="ad088-107">[Microsoft][ODBC Cursor Library]</span><span class="sxs-lookup"><span data-stu-id="ad088-107">[Microsoft][ODBC Cursor Library]</span></span>  
 <span data-ttu-id="ad088-108">이러한 오류는 ODBC 커서 라이브러리에서 발생됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad088-108">These errors are raised by the ODBC cursor library.</span></span>  
  
 <span data-ttu-id="ad088-109">[Microsoft][SQL Server Native Client]</span><span class="sxs-lookup"><span data-stu-id="ad088-109">[Microsoft][SQL Server Native Client]</span></span>  
 <span data-ttu-id="ad088-110">이러한 오류는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 드라이버에 의해 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad088-110">These errors are raised by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="ad088-111">이름이 Net-Library 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인 다른 노드가 없으면 드라이버에서 오류가 발생한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ad088-111">If there are no other nodes with either the name of a Net-Library or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], then the error was encountered in the driver.</span></span>  
  
 <span data-ttu-id="ad088-112">Microsoft [SQL Server Native Client] [*네트워크-이름*]</span><span class="sxs-lookup"><span data-stu-id="ad088-112">[Microsoft][SQL Server Native Client][*Net-Transportname*]</span></span>  
 <span data-ttu-id="ad088-113">이러한 오류는 Net-library에 의해 발생 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 합니다. 여기서 *net-udname* 은 클라이언트 네트워크 전송의 표시 이름 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (예: 명명 된 파이프, 공유 메모리, tcp/ip 소켓 또는 VIA)입니다.</span><span class="sxs-lookup"><span data-stu-id="ad088-113">These errors are raised by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Net-Library, where *Net-Transportname* is the display name of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client network transport (for example, Named Pipes, Shared Memory, TCP/IP Sockets, or VIA).</span></span> <span data-ttu-id="ad088-114">나머지 오류 메시지에는 호출된 Net-Library 함수 및 TDS 함수에 의해 기본 네트워크 API에서 호출된 함수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad088-114">The remainder of the error message contains the Net-Library function called and the function called in the underlying network API by the TDS function.</span></span> <span data-ttu-id="ad088-115">이러한 오류와 함께 반환 되는 *pfNative* 오류 코드는 기본 네트워크 프로토콜 스택의 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="ad088-115">The *pfNative* error code returned with these errors is the error code from the underlying network protocol stack.</span></span>  
  
 <span data-ttu-id="ad088-116">[Microsoft][SQL Server Native Client][[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]]</span><span class="sxs-lookup"><span data-stu-id="ad088-116">[Microsoft][SQL Server Native Client][[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]]</span></span>  
 <span data-ttu-id="ad088-117">이러한 오류는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 발생됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad088-117">These errors are raised by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ad088-118">나머지 오류 메시지는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 오류 메시지 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="ad088-118">The remainder of the error message is the text of the error message from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ad088-119">이러한 오류와 함께 반환 되는 *pfNative* 코드는의 오류 번호입니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ad088-119">The *pfNative* code returned with these errors is the error number from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ad088-120">에서 반환 될 수 있는 오류 메시지 목록 및 오류 메시지에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 **master** 데이터베이스에서 **sysmessages** 시스템 테이블의 설명 및 오류 열을 참조 하세요 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ad088-120">For more information about a list of error messages (and their numbers) that can be returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see the description and error columns of the **sysmessages** system table in the **master** database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad088-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ad088-121">See Also</span></span>  
 [<span data-ttu-id="ad088-122">오류 및 메시지 처리</span><span class="sxs-lookup"><span data-stu-id="ad088-122">Handling Errors and Messages</span></span>](handling-errors-and-messages.md)  
  
  

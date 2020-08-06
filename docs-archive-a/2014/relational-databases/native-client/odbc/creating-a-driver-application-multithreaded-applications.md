---
title: 다중 스레드 응용 프로그램 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- threads [SQL Server], multithreaded applications
- ODBC applications, multithreaded applications
- asynchronous operations [SQL Server Native Client]
- SQL Server Native Client ODBC driver, multithreaded applications
- multithreaded applications [SQL Server Native Client]
ms.assetid: d352c91a-6e08-4e50-9f3e-a37892d9c2cc
author: rothja
ms.author: jroth
ms.openlocfilehash: b680086f76e0c1a1e8c8cfc2f4ef82099957b3fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653298"
---
# <a name="multithreaded-applications"></a><span data-ttu-id="67859-102">다중 스레드 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="67859-102">Multithreaded Applications</span></span>
  <span data-ttu-id="67859-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 다중 스레드 드라이버입니다.</span><span class="sxs-lookup"><span data-stu-id="67859-103">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver is a multithreaded driver.</span></span> <span data-ttu-id="67859-104">다중 스레드 애플리케이션을 작성하면 여러 ODBC 호출을 처리하기 위해 비동기 호출을 사용하는 방법을 대신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67859-104">Writing a multithreaded application is an alternative to using asynchronous calls to process multiple ODBC calls.</span></span> <span data-ttu-id="67859-105">스레드는 동기 ODBC 호출을 실행할 수 있으며 다른 스레드는 첫 번째 스레드가 호출에 대한 응답을 대기하면서 차단되는 동안 처리될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67859-105">A thread can make a synchronous ODBC call, and other threads can process while the first thread is blocked waiting for the response to its call.</span></span> <span data-ttu-id="67859-106">이 모델을 사용하면 네트워크 트래픽 및 SQL_STILL_EXECUTING을 테스트하기 위한 ODBC 함수의 반복적인 호출로 인해 발생하는 오버헤드 문제를 해결할 수 있기 때문에 비동기 호출을 실행하는 것보다 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="67859-106">This model is more efficient than making asynchronous calls because it eliminates overhead such as network traffic and making repeated ODBC function calls testing for SQL_STILL_EXECUTING.</span></span>  
  
 <span data-ttu-id="67859-107">그러나 비동기 모드는 여전히 효과적인 처리 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="67859-107">Asynchronous mode is still an effective method of processing.</span></span> <span data-ttu-id="67859-108">다중 스레드 모델의 성능이 크게 향상되기는 했지만 비동기 애플리케이션을 다시 작성해야 할 정도는 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="67859-108">The performance improvements of a multithreaded model are not enough to justify rewriting asynchronous applications.</span></span> <span data-ttu-id="67859-109">DB-Library 비동기 모델을 사용하는 DB-Library 애플리케이션을 변환하는 경우에는 애플리케이션을 ODBC 비동기 모델로 변환하는 것이 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="67859-109">If users are converting DB-Library applications that use the DB-Library asynchronous model, it is easier to convert them to the ODBC asynchronous model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67859-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="67859-110">See Also</span></span>  
 [<span data-ttu-id="67859-111">SQL Server Native Client ODBC 드라이버 애플리케이션 만들기</span><span class="sxs-lookup"><span data-stu-id="67859-111">Creating a SQL Server Native Client ODBC Driver Application</span></span>](creating-a-driver-application.md)  
  
  

---
title: SQLNativeSql | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLNativeSql function
ms.assetid: 2d999fec-9e22-4514-ad5f-22a64b82f95b
author: rothja
ms.author: jroth
ms.openlocfilehash: 433b086dc36a79cb82868edebac9f0a4814c21fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660531"
---
# <a name="sqlnativesql"></a><span data-ttu-id="58f10-102">SQLNativeSql</span><span class="sxs-lookup"><span data-stu-id="58f10-102">SQLNativeSql</span></span>
  <span data-ttu-id="58f10-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 서버를 방문하지 않고 **SQLNativeSql** 요청을 충족합니다.</span><span class="sxs-lookup"><span data-stu-id="58f10-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver satisfies **SQLNativeSql** requests without visiting the server.</span></span> <span data-ttu-id="58f10-104">이 함수는 SQL 문의 구문을 효율적으로 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="58f10-104">The function efficiently tests the syntax of SQL statements.</span></span> <span data-ttu-id="58f10-105">구문 검사는 SQL 문의 식 결과나 식별자가 유효한지 여부를 확인하지 않으며, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQLNativeSql **에서 반환된** 네이티브 SQL이 실행되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58f10-105">Syntax checking does not determine if identifiers or the results of expressions in the SQL statements are valid, and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native SQL returned by **SQLNativeSql** can fail to run.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58f10-106">참고 항목</span><span class="sxs-lookup"><span data-stu-id="58f10-106">See Also</span></span>  
 <span data-ttu-id="58f10-107">[SQLNativeSql 함수](https://go.microsoft.com/fwlink/?LinkID=59358) </span><span class="sxs-lookup"><span data-stu-id="58f10-107">[SQLNativeSql Function](https://go.microsoft.com/fwlink/?LinkID=59358) </span></span>  
 [<span data-ttu-id="58f10-108">ODBC API 구현 정보</span><span class="sxs-lookup"><span data-stu-id="58f10-108">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  

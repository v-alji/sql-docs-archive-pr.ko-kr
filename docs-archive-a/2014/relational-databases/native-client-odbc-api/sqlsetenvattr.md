---
title: SQLSetEnvAttr | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLSetEnvAttr function
ms.assetid: d4114571-feca-4330-b2e4-7bfd1050b812
author: rothja
ms.author: jroth
ms.openlocfilehash: f0dbd4d01de9ca769c46a93f810f0149f5b86981
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660509"
---
# <a name="sqlsetenvattr"></a><span data-ttu-id="1c777-102">SQLSetEnvAttr</span><span class="sxs-lookup"><span data-stu-id="1c777-102">SQLSetEnvAttr</span></span>
  <span data-ttu-id="1c777-103">[ODBC 프로그래머 참조(ODBC Programmer's Reference)](https://go.microsoft.com/fwlink/?LinkId=45250) 에는 ODBC 2. **x** 또는 ODBC 3.*x* API를 사용하도록 작성된 애플리케이션에서 ODBC 드라이버가*SQLSetEnvAttr* 특성 사양을 해석하는 방법이 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c777-103">The [ODBC Programmer's Reference](https://go.microsoft.com/fwlink/?LinkId=45250) defines how ODBC drivers should interpret the **SQLSetEnvAttr** attribute specifications from applications written to either the ODBC 2.*x* or ODBC 3.*x* API.</span></span> <span data-ttu-id="1c777-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 이러한 규칙을 준수합니다.</span><span class="sxs-lookup"><span data-stu-id="1c777-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver complies with those rules.</span></span>  
  
 <span data-ttu-id="1c777-105">**SQLSetEnvAttr** 은 연결 풀링을 사용할지 여부를 제어하는 특성 중 하나를 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="1c777-105">One of the attributes controlled by **SQLSetEnvAttr** is whether connection pooling is to be used.</span></span> <span data-ttu-id="1c777-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버에 연결 풀링을 사용하려면 *SQLDriverConnect* 또는 [SQLConnect](sqldriverconnect.md) 를 사용하여 연결할 때 **DriverCompletion**매개 변수를 SQL_DRIVER_NOPROMPT로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c777-106">If connection pooling is used with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver, the *DriverCompletion* parameter must be set to SQL_DRIVER_NOPROMPT when connecting with either [SQLDriverConnect](sqldriverconnect.md) or **SQLConnect**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c777-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1c777-107">See Also</span></span>  
 <span data-ttu-id="1c777-108">[SQLSetEnvAttr 함수](https://go.microsoft.com/fwlink/?LinkId=59369) </span><span class="sxs-lookup"><span data-stu-id="1c777-108">[SQLSetEnvAttr Function](https://go.microsoft.com/fwlink/?LinkId=59369) </span></span>  
 [<span data-ttu-id="1c777-109">ODBC API 구현 정보</span><span class="sxs-lookup"><span data-stu-id="1c777-109">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  

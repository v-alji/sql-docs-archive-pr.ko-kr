---
title: 데이터 원본 삭제 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: 910e3e16-7b91-49d8-80bb-b4243926afaa
author: rothja
ms.author: jroth
ms.openlocfilehash: 6e8acd6414b39b317ff0fcfe1b7b9fbab38ae0a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649040"
---
# <a name="delete-a-data-source-odbc"></a><span data-ttu-id="5b3f9-102">데이터 원본 삭제(ODBC)</span><span class="sxs-lookup"><span data-stu-id="5b3f9-102">Delete a Data Source (ODBC)</span></span>
  <span data-ttu-id="5b3f9-103">ODBC 관리자를 사용 하 여 프로그래밍 방식으로 ( [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)사용) 또는 파일 (파일 데이터 원본 이름)을 삭제 하 여 데이터 원본을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f9-103">You can delete a data source by using ODBC Administrator, programmatically (by using [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)), or by deleting a file (if a file data source name).</span></span>  
  
### <a name="to-delete-a-data-source-by-using-odbc-administrator"></a><span data-ttu-id="5b3f9-104">ODBC 관리자를 사용하여 데이터 원본을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="5b3f9-104">To delete a data source by using ODBC Administrator</span></span>  
  
1.  <span data-ttu-id="5b3f9-105">**제어판**에서 **관리 도구**를 연 다음 **데이터 원본 (ODBC)** 을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f9-105">In **Control Panel**, open **Administrative Tools**, and then double-click **Data Sources (ODBC)**.</span></span> <span data-ttu-id="5b3f9-106">또는 명령 프롬프트에서 odbcad32.exe를 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f9-106">Alternatively, you can run odbcad32.exe from the command prompt.</span></span>  
  
2.  <span data-ttu-id="5b3f9-107">**사용자 dsn**, **시스템 DSN**또는 **파일 dsn** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f9-107">Click the **User DSN**, **System DSN**, or **File DSN** tab.</span></span>  
  
3.  <span data-ttu-id="5b3f9-108">삭제할 데이터 원본을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f9-108">Click the data source to delete.</span></span>  
  
4.  <span data-ttu-id="5b3f9-109">**제거**를 클릭 한 다음 삭제를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f9-109">Click **Remove**, and then confirm the deletion.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b3f9-110">예제</span><span class="sxs-lookup"><span data-stu-id="5b3f9-110">Example</span></span>  
 <span data-ttu-id="5b3f9-111">데이터 원본을 프로그래밍 방식으로 삭제 하려면 ODBC_REMOVE_DSN 또는 ODBC_REMOVE_SYS_DSN를 두 번째 매개 변수로 사용 하 여 [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) 를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f9-111">To programmatically delete a data source, call [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) using either ODBC_REMOVE_DSN or ODBC_REMOVE_SYS_DSN as the second parameter.</span></span>  
  
 <span data-ttu-id="5b3f9-112">다음 예에서는 데이터 원본을 프로그래밍 방식으로 삭제하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f9-112">The following sample shows how you can programmatically delete a data source.</span></span>  
  
```  
// remove_odbc_data_source.cpp  
// compile with: ODBCCP32.lib user32.lib  
#include <iostream>  
#include <windows.h>  
#include <odbcinst.h>  
  
int main() {   
   LPCSTR provider = "SQL Server";   // Windows SQL Server Driver  
   LPCSTR provider = "SQL Server";   // Windows SQL Server driver  
   LPCSTR provider2 = "SQL Server Native Client 11.0";   // SQL Server 2012 Native Client driver  
   LPCSTR dsnname = "DSN=data2";  
   BOOL retval = SQLConfigDataSource(NULL, ODBC_REMOVE_DSN, provider, dsnname);  
   std::cout << retval;   // 1 if successful  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="5b3f9-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5b3f9-113">See Also</span></span>  
 [<span data-ttu-id="5b3f9-114">SQL Server ODBC 드라이버 구성 방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="5b3f9-114">Configuring the SQL Server ODBC Driver How-to Topics</span></span>](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  

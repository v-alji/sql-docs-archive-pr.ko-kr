---
title: 데이터 원본 추가 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: b4ac6f0e-8e6a-4b1a-9a7e-60e0a69b2180
author: rothja
ms.author: jroth
ms.openlocfilehash: 519990e9dd9d84f75c4efc6c76b910f0a359f52f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649042"
---
# <a name="add-a-data-source-odbc"></a><span data-ttu-id="3934f-102">데이터 원본 추가(ODBC)</span><span class="sxs-lookup"><span data-stu-id="3934f-102">Add a Data Source (ODBC)</span></span>
  <span data-ttu-id="3934f-103">ODBC 관리자를 사용 하 여 프로그래밍 방식으로 ( [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)사용) 또는 파일을 만들어 데이터 원본을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3934f-103">You can add a data source by using ODBC Administrator, programmatically (by using [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)), or by creating a file.</span></span>  
  
### <a name="to-add-a-data-source-by-using-odbc-administrator"></a><span data-ttu-id="3934f-104">ODBC 관리자를 사용하여 데이터 원본을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="3934f-104">To add a data source by using ODBC Administrator</span></span>  
  
1.  <span data-ttu-id="3934f-105">**제어판**에서 **관리 도구** , **데이터 원본 (ODBC)** 에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="3934f-105">From the **Control Panel**, access **Administrative Tools** and then **Data Sources (ODBC)**.</span></span> <span data-ttu-id="3934f-106">또는 odbcad32.exe를 호출할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3934f-106">Alternatively, you can invoke odbcad32.exe.</span></span>  
  
2.  <span data-ttu-id="3934f-107">**사용자 dsn**, **시스템 DSN**또는 **파일 dsn** 탭을 클릭 한 다음 **추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="3934f-107">Click the **User DSN**, **System DSN**, or **File DSN** tab, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="3934f-108">**SQL Server**를 클릭 한 다음 **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="3934f-108">Click **SQL Server**, and then click **Finish**.</span></span>  
  
4.  <span data-ttu-id="3934f-109">SQL Server에 새로운 데이터 원본 만들기 마법사의 각 단계를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="3934f-109">Complete the Steps in the Create a New Data Source to SQL Server Wizard.</span></span>  
  
### <a name="to-add-a-data-source-programmatically"></a><span data-ttu-id="3934f-110">프로그래밍 방식으로 데이터 원본을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="3934f-110">To add a data source programmatically</span></span>  
  
1.  <span data-ttu-id="3934f-111">ODBC_ADD_DSN 또는 ODBC_ADD_SYS_DSN로 설정 된 두 번째 매개 변수를 사용 하 여 [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) 를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="3934f-111">Call [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) with the second parameter set to either ODBC_ADD_DSN or ODBC_ADD_SYS_DSN.</span></span>  
  
### <a name="to-add-a-file-data-source"></a><span data-ttu-id="3934f-112">파일 데이터 원본을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="3934f-112">To add a file data source</span></span>  
  
1.  <span data-ttu-id="3934f-113">연결 문자열에서 SAVEFILE = file_name 매개 변수를 사용 하 여 [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) 를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="3934f-113">Call [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) with a SAVEFILE=file_name parameter in the connect string.</span></span> <span data-ttu-id="3934f-114">연결에 성공하면 ODBC 드라이버가 연결 매개 변수를 사용하여 SAVEFILE 매개 변수가 가리키는 위치에 파일 데이터 원본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3934f-114">If the connect is successful, the ODBC driver creates a file data source with the connection parameters in the location pointed to by the SAVEFILE parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3934f-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3934f-115">See Also</span></span>  
 [<span data-ttu-id="3934f-116">SQL Server ODBC 드라이버 구성 방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="3934f-116">Configuring the SQL Server ODBC Driver How-to Topics</span></span>](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  

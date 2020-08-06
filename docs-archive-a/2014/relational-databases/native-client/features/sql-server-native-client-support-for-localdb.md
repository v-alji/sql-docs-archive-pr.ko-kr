---
title: LocalDB에 대 한 SQL Server Native Client 지원 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 127569d1-a9f7-49bf-a561-c084986a8871
author: rothja
ms.author: jroth
ms.openlocfilehash: b08ea46e8db1b665280116a439b95748f69d03ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648357"
---
# <a name="sql-server-native-client-support-for-localdb"></a><span data-ttu-id="7072f-102">LocalDB에 대한 SQL Server Native Client 지원</span><span class="sxs-lookup"><span data-stu-id="7072f-102">SQL Server Native Client Support for LocalDB</span></span>
  <span data-ttu-id="7072f-103">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]부터는 LocalDB라고 부르는 SQL Server의 경량 버전을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7072f-103">Beginning in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], a lightweight version of SQL Server, called LocalDB, will be available.</span></span> <span data-ttu-id="7072f-104">이 항목에서는 LocalDB 인스턴스의 데이터베이스에 연결하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7072f-104">This topic discusses how to connect to a database in a LocalDB instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7072f-105">설명</span><span class="sxs-lookup"><span data-stu-id="7072f-105">Remarks</span></span>  
 <span data-ttu-id="7072f-106">LocalDB 설치 및 LocalDB 인스턴스 구성 방법을 포함하여 LocalDB에 대한 자세한 내용은 다음을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7072f-106">For more information about LocalDB, including how to install LocalDB and configure your LocalDB instance, see:</span></span>  
  
-   [<span data-ttu-id="7072f-107">SQL Server Express LocalDB 참조</span><span class="sxs-lookup"><span data-stu-id="7072f-107">SQL Server Express LocalDB Reference</span></span>](../../sql-server-express-localdb-reference.md)  
  
-   [<span data-ttu-id="7072f-108">SQL Server 2014 Express LocalDB</span><span class="sxs-lookup"><span data-stu-id="7072f-108">SQL Server 2014 Express LocalDB</span></span>](../../../database-engine/configure-windows/sql-server-2016-express-localdb.md)  
  
 <span data-ttu-id="7072f-109">요약하자면, LocalDB를 통해 다음과 같은 기능을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7072f-109">To summarize, LocalDB allows you to:</span></span>  
  
-   <span data-ttu-id="7072f-110">`sqllocaldb.exe i`를 사용하여 기본 인스턴스의 이름을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7072f-110">Use `sqllocaldb.exe i` to discover the name of the default instance.</span></span>  
  
-   <span data-ttu-id="7072f-111">`AttachDBFilename` 연결 문자열 키워드를 사용하여 서버가 연결해야 하는 데이터베이스 파일을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7072f-111">Use the `AttachDBFilename` connection string keyword to specify which database file the server should attach.</span></span> <span data-ttu-id="7072f-112">를 사용 하는 경우 데이터베이스 연결 문자열 키워드를 사용 하 여 `AttachDBFilename` 데이터베이스 이름을 **Database** 지정 하지 않으면 응용 프로그램이 닫힐 때 LocalDB 인스턴스에서 데이터베이스가 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7072f-112">When using `AttachDBFilename`, if you do not specify the name of the database with the **Database** connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
-   <span data-ttu-id="7072f-113">연결 문자열에 LocalDB 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7072f-113">Specify a LocalDB instance in your connection string:</span></span>  
  
```  
SERVER=(localdb)\v11.0  
```  
  
 <span data-ttu-id="7072f-114">필요한 경우 sqllocaldb.exe를 사용하여 LocalDB 인스턴스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7072f-114">If necessary, you can create a LocalDB instance with sqllocaldb.exe.</span></span> <span data-ttu-id="7072f-115">또한 sqlcmd.exe를 사용하여 LocalDB 인스턴스에서 데이터베이스를 추가하고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7072f-115">You can also use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="7072f-116">`sqlcmd -S (localdb)\v11.0`)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7072f-116">For example, `sqlcmd -S (localdb)\v11.0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7072f-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7072f-117">See Also</span></span>  
 [<span data-ttu-id="7072f-118">SQL Server Native Client 기능</span><span class="sxs-lookup"><span data-stu-id="7072f-118">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  

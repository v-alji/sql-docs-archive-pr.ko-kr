---
title: SQL Server Native Client를 사용 하 여 Azure SQL Database에 연결 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 0dc20bb6-b142-4259-b87b-427d2ba798af
author: rothja
ms.author: jroth
ms.openlocfilehash: 177c655f97e32f2044460e87c6cd775cdf8fcde9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652072"
---
# <a name="connecting-to-an-azure-sql-database-using-sql-server-native-client"></a><span data-ttu-id="e8b7c-102">SQL Server Native Client를 사용하여 Azure SQL Database에 연결</span><span class="sxs-lookup"><span data-stu-id="e8b7c-102">Connecting to an Azure SQL Database Using SQL Server Native Client</span></span>
  <span data-ttu-id="e8b7c-103">Native Client를 사용 하 여에 연결 하는 방법을 보여 주는 샘플은 [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [개발: 방법 도움말 항목 (Azure SQL Database)](https://msdn.microsoft.com/library/ee621787.aspx)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8b7c-103">For a sample that shows how to connect to a [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, see [Development: How-to Topics (Azure SQL Database)](https://msdn.microsoft.com/library/ee621787.aspx).</span></span>  
  
## <a name="known-issues-when-connecting-to-a-sql-database"></a><span data-ttu-id="e8b7c-104">SQL Database에 연결할 때 알려진 문제</span><span class="sxs-lookup"><span data-stu-id="e8b7c-104">Known Issues When Connecting to a SQL Database</span></span>  
 <span data-ttu-id="e8b7c-105">다음은 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] Native Client를 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 연결할 때 알려진 문제입니다.</span><span class="sxs-lookup"><span data-stu-id="e8b7c-105">The following are known issues when connecting to a [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client:</span></span>  
  
-   <span data-ttu-id="e8b7c-106">단계에 `SQLBrowseConnect`가 사용되는 경우 `SQLBrowseConnect`를 사용한 연결은 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8b7c-106">A connection made with `SQLBrowseConnect` may be rejected if `SQLBrowseConnect` is used in stages.</span></span>  <span data-ttu-id="e8b7c-107">예를 들어 첫 번째 호출에서 드라이버 이름을 보내고, 두 번째 호출에서 서버 및 자격 증명(사용자 및 암호)을 보내 연결을 설정하고, 세 번째 호출에서 데이터베이스 이름 및 언어를 보내는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="e8b7c-107">For example, if the driver name is sent in the first call, server and credentials (user and password) sent in the second call, establishing the connection, and a database name and a language in the third call.</span></span>  <span data-ttu-id="e8b7c-108">세 번째 호출은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client가 USE 문을 실행하여 데이터베이스를 변경하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b7c-108">The third call will cause [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client to issue a USE statement to change databases.</span></span> <span data-ttu-id="e8b7c-109">그러나 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]에서 USE 문이 지원되지 않으므로 다음과 같은 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b7c-109">However, the USE statement is not supported in [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], generating the following error:</span></span>  
  
    ```  
    [Microsoft][SQL Server Native Client 11.0][SQL Server]USE statement is not supported to switch between databases. Use a new connection to connect to a different Database.  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e8b7c-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e8b7c-110">See Also</span></span>  
 [<span data-ttu-id="e8b7c-111">SQL Server Native Client를 사용하여 애플리케이션 빌드</span><span class="sxs-lookup"><span data-stu-id="e8b7c-111">Building Applications with SQL Server Native Client</span></span>](building-applications-with-sql-server-native-client.md)  
  
  

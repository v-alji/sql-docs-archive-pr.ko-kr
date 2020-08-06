---
title: 고급 연결 속성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4edfab68-7e68-45e8-a3f3-a0049ff7eb9e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8dc844d1fdfb1e82f0ffa8de93a6a1060ef190cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652980"
---
# <a name="advanced-connection-properties"></a><span data-ttu-id="73a47-102">고급 연결 속성</span><span class="sxs-lookup"><span data-stu-id="73a47-102">Advanced Connection Properties</span></span>
  <span data-ttu-id="73a47-103">**고급 연결 속성** 대화 상자를 사용하여 연결 문자열에 연결 매개 변수를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73a47-103">Use the **Advanced Connection Properties** dialog box to add more connection parameters to the connection string.</span></span>  
  
 <span data-ttu-id="73a47-104">사용 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에서 지원되는 모든 ODBC 연결 매개 변수를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73a47-104">The additional connection parameters can be any ODBC connection parameter that is supported by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database instance you are using.</span></span>  
  
 <span data-ttu-id="73a47-105">**고급 연결 속성** 대화 상자를 사용하여 추가한 매개 변수는 **SQL Server에 연결** 대화 상자에서 선택한 매개 변수에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="73a47-105">The parameters added using the **Advanced Connection Properties** dialog box are added to the parameters selected in the **Connect to SQL Server** dialog box.</span></span>  
  
 <span data-ttu-id="73a47-106">제공된 각 매개 변수의 마지막 인스턴스는 매개 변수의 이전 인스턴스보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="73a47-106">The last instance of each parameter provided overrides any previous instances of the parameter.</span></span> <span data-ttu-id="73a47-107">**고급 연결 매개 변수** 대화 상자를 사용하여 추가한 매개 변수가 그 다음이고 **SQL Server 연결** 대화 상자에서 제공한 매개 변수를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="73a47-107">Parameters added using the **Advanced Connection Parameters** dialog box follow and replace the parameters provided in the **SQL Server Connection** dialog box.</span></span> <span data-ttu-id="73a47-108">예를 들어 **SQL Server 연결** 대화 상자에서 SERVER1을 서버 이름으로 지정하고 **추가 연결 매개 변수** 페이지에 ;SERVER=SERVER2가 있으면 SERVER2에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="73a47-108">For example, if the **SQL Server Connection** dialog box specifies SERVER1 as the Server name, and the **Additional Connection Parameters** page contains ;SERVER=SERVER2, the connection will be made to SERVER2.</span></span>  
  
 <span data-ttu-id="73a47-109">**고급 연결 속성** 대화 상자를 사용하여 추가한 매개 변수는 일반 텍스트로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="73a47-109">Parameters added using the **Advanced Connection Properties** dialog box are passed as plain text.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="73a47-110">**고급 연결 속성** 대화 상자에 로그인 자격 증명을 포함하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="73a47-110">Do not include login credentials in the **Advanced Connection Properties** dialog box.</span></span> <span data-ttu-id="73a47-111">이러한 정보는 네트워크로 전달될 때 암호화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="73a47-111">They will not be encrypted when they are passed across the network.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73a47-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="73a47-112">See Also</span></span>  
 <span data-ttu-id="73a47-113">[CDC Designer 콘솔 액세스](access-the-cdc-designer-console.md) </span><span class="sxs-lookup"><span data-stu-id="73a47-113">[Access the CDC Designer Console](access-the-cdc-designer-console.md) </span></span>  
 [<span data-ttu-id="73a47-114">인스턴스를 만들기 위한 SQL Server 연결</span><span class="sxs-lookup"><span data-stu-id="73a47-114">SQL Server Connection for Instance Creation</span></span>](sql-server-connection-for-instance-creation.md)  
  
  

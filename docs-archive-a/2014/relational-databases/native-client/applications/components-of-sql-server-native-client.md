---
title: SQL Server Native Client의 구성 요소 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- data access [SQL Server Native Client], components
- components [SQL Server Native Client]
- SQLNCLI, about SQL Server Native Client
ms.assetid: 65f932d5-daa1-4eff-b6df-ee633fcf2a7c
author: rothja
ms.author: jroth
ms.openlocfilehash: 32438b9fb5473d9251acd0aceddb46db373f3548
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652075"
---
# <a name="components-of-sql-server-native-client"></a><span data-ttu-id="b725b-102">SQL Server Native Client의 구성 요소</span><span class="sxs-lookup"><span data-stu-id="b725b-102">Components of SQL Server Native Client</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="b725b-103">Native Client에는 다음 구성 요소가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b725b-103">Native Client contains the following components:</span></span>  
  
|<span data-ttu-id="b725b-104">구성 요소</span><span class="sxs-lookup"><span data-stu-id="b725b-104">Component</span></span>|<span data-ttu-id="b725b-105">Description</span><span class="sxs-lookup"><span data-stu-id="b725b-105">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b725b-106">sqlncli11.dll</span><span class="sxs-lookup"><span data-stu-id="b725b-106">sqlncli11.dll</span></span>|<span data-ttu-id="b725b-107">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 기능이 모두 포함된 DLL(동적 연결 라이브러리) 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="b725b-107">The dynamic-link library (DLL) file that contains all of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client functionality.</span></span> <span data-ttu-id="b725b-108">여기에는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB Provider와 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b725b-108">This includes the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider and the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>|  
|<span data-ttu-id="b725b-109">sqlnclir11.rll</span><span class="sxs-lookup"><span data-stu-id="b725b-109">sqlnclir11.rll</span></span>|<span data-ttu-id="b725b-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 라이브러리에 대한 리소스 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="b725b-110">The accompanying resource file for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client library.</span></span>|  
|<span data-ttu-id="b725b-111">s10ch_sqlncli.chm</span><span class="sxs-lookup"><span data-stu-id="b725b-111">s10ch_sqlncli.chm</span></span>|<span data-ttu-id="b725b-112">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버나 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB Provider를 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 원본을 만드는 방법을 문서화하는 데이터 원본 마법사 도움말 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="b725b-112">The Data Source Wizard help file that documents how to create a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data source using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver or the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span>|  
|<span data-ttu-id="b725b-113">sqlncli.h</span><span class="sxs-lookup"><span data-stu-id="b725b-113">sqlncli.h</span></span>|<span data-ttu-id="b725b-114">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client를 사용하는 데 필요한 모든 새 정의가 포함된 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 헤더 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="b725b-114">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client header file that contains all of the new definitions needed in order to use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="b725b-115">이 헤더 파일은 odbcss.h 및 sqloledb.h 헤더 파일을 모두 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="b725b-115">This header file replaces both the odbcss.h and the sqloledb.h header files.</span></span> <span data-ttu-id="b725b-116">**참고:**  동일한 프로그램에서 sqlncli 및 odbcss.h를 참조할 수 없지만, 먼저 sqloledb가 정의 되어 있는 한 동일한 프로그램에서 sqlncli 및 sqloledb를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b725b-116">**Note:**  You cannot reference sqlncli.h and odbcss.h in the same program, but you can reference sqlncli.h and sqloledb.h in same program as long as sqloledb.h is defined first.</span></span>|  
|<span data-ttu-id="b725b-117">sqlncli11.lib</span><span class="sxs-lookup"><span data-stu-id="b725b-117">sqlncli11.lib</span></span>|<span data-ttu-id="b725b-118">Native Client ODBC 드라이버의 일부인 **bcp** 유틸리티 함수를 직접 호출 하는 데 필요한 라이브러리 파일 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 입니다.</span><span class="sxs-lookup"><span data-stu-id="b725b-118">The library file needed to directly call the **bcp** utility functions that are part of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="b725b-119">**참고:**  프로그래밍 코드의 sqlncli11 파일을 참조 하는 경우에는 sqlncli11.dll 파일이 시스템 경로 및 응용 프로그램을 사용 하는 사용자의 시스템 경로에 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b725b-119">**Note:**  If you do reference the sqlncli11.lib file in your programming code, you need to make sure that the sqlncli11.dll file is in your system path, and in the system path of the users that make use of your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b725b-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b725b-120">See Also</span></span>  
 [<span data-ttu-id="b725b-121">SQL Server Native Client를 사용하여 애플리케이션 빌드</span><span class="sxs-lookup"><span data-stu-id="b725b-121">Building Applications with SQL Server Native Client</span></span>](building-applications-with-sql-server-native-client.md)  
  
  

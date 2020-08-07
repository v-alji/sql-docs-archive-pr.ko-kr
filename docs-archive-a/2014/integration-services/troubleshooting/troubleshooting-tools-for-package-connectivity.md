---
title: 도구 패키지 연결 문제 해결 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Integration Services packages, troubleshooting
- SSIS packages, troubleshooting
- Integration Services, troubleshooting
- connectivity [Integration Services], troubleshooting
- errors [Integration Services], troubleshooting
- packages [Integration Services], troubleshooting
ms.assetid: 08a019f5-8ba7-4527-97c1-e9846d4022ff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1baac9af5a30fdc0f5b15e8ac56eb5badacc0edb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731875"
---
# <a name="troubleshooting-tools-package-connectivity"></a><span data-ttu-id="358de-102">패키지 연결 문제 해결 도구</span><span class="sxs-lookup"><span data-stu-id="358de-102">Troubleshooting Tools Package Connectivity</span></span>
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]<span data-ttu-id="358de-103">는 패키지와 패키지가 데이터를 추출 및 로드하는 데이터 원본 간 연결 문제를 해결하는 데 사용할 수 있는 기능 및 도구를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="358de-103">includes features and tools that you can use to troubleshoot connectivity between packages and the data sources from which packages extract and load data.</span></span>  
  
## <a name="troubleshooting-issues-with-external-data-providers"></a><span data-ttu-id="358de-104">외부 데이터 공급자와의 문제 해결</span><span class="sxs-lookup"><span data-stu-id="358de-104">Troubleshooting Issues with External Data Providers</span></span>  
 <span data-ttu-id="358de-105">다수의 패키지 오류가 외부 데이터 공급자와 상호 작용하는 동안 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="358de-105">Many packages fail during interactions with external data providers.</span></span> <span data-ttu-id="358de-106">하지만 이러한 공급자가 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 로 반환하는 메시지에서 상호 작용 문제 해결을 시작하기에 충분한 정보를 제공하지 않는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="358de-106">However, the messages that those providers return to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] frequently do not provide enough information to start troubleshooting the interaction.</span></span> <span data-ttu-id="358de-107">이 문제 해결 요구를 다루기 위해 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 에는 외부 데이터 원본과의 패키지 상호 작용 문제를 해결하는 데 사용할 수 있는 로깅 메시지가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="358de-107">To address this troubleshooting need, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes logging messages that you can use to troubleshoot a package's interaction with external data sources.</span></span>  
  
-   <span data-ttu-id="358de-108">**로깅을 설정하고 패키지의 Diagnostic 이벤트를 선택하여 문제 해결 메시지를 표시합니다**.</span><span class="sxs-lookup"><span data-stu-id="358de-108">**Enable logging and select the package's Diagnostic event to see the troubleshooting messages**.</span></span> <span data-ttu-id="358de-109">다음 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 구성 요소는 외부 데이터 공급자 호출 전후에 메시지를 로그에 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="358de-109">The following [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components are capable of writing a message to the log before and after every call to an external data provider:</span></span>  
  
    -   <span data-ttu-id="358de-110">OLE DB 연결 관리자, OLE DB 원본 및 OLE DB 대상</span><span class="sxs-lookup"><span data-stu-id="358de-110">OLE DB connection manager, OLE DB source, and OLE DB destination</span></span>  
  
    -   [!INCLUDE[vstecado](../../includes/vstecado-md.md)] <span data-ttu-id="358de-111">연결 관리자 및 ADO.NET 원본</span><span class="sxs-lookup"><span data-stu-id="358de-111">connection manager and ADO NET source</span></span>  
  
    -   <span data-ttu-id="358de-112">SQL 실행 태스크</span><span class="sxs-lookup"><span data-stu-id="358de-112">Execute SQL task</span></span>  
  
    -   <span data-ttu-id="358de-113">조회 변환, OLE DB 명령 변환 및 느린 변경 차원 변환</span><span class="sxs-lookup"><span data-stu-id="358de-113">Lookup transformation, OLE DB Command transformation, and Slowly Changing Dimension transformation</span></span>  
  
     <span data-ttu-id="358de-114">로그 메시지에는 호출되는 메서드의 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="358de-114">The log messages include the name of the method being called.</span></span> <span data-ttu-id="358de-115">예를 들어 이러한 로그 메시지에 OLE DB `Open` 개체의 `Connection` 메서드나 `ExecuteNonQuery` 개체의 `Command` 메서드가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="358de-115">For example, these log messages might include the `Open` method of an OLE DB `Connection` object or the `ExecuteNonQuery` method of a `Command` object.</span></span> <span data-ttu-id="358de-116">메시지의 형식은 다음과 같습니다. 여기서</span><span class="sxs-lookup"><span data-stu-id="358de-116">The messages have the following format, where '%1!s!'</span></span> <span data-ttu-id="358de-117">'%1!s!'는 메서드 정보에 대한 자리 표시자입니다.</span><span class="sxs-lookup"><span data-stu-id="358de-117">is a placeholder for the method information:</span></span>  
  
    ```  
    ExternalRequest_pre: The object is ready to make the following external request: '%1!s!'.  
    ExternalRequest_post: '%1!s!'. The external request has completed.  
    ```  
  
     <span data-ttu-id="358de-118">외부 데이터 공급자와의 상호 작용 문제를 해결하려면 로그를 검토하여 모든 "호출 전" 메시지(`ExternalRequest_pre`)에 해당하는 "호출 후" 메시지(`ExternalRequest_post`)가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="358de-118">To troubleshoot the interaction with the external data provider, review the log to see whether every "before" message (`ExternalRequest_pre`) has a corresponding "after" message (`ExternalRequest_post`).</span></span> <span data-ttu-id="358de-119">해당하는 "호출 후" 메시지가 없으면 외부 데이터 공급자가 예상대로 응답하지 않은 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="358de-119">If there is no corresponding "after" message, you know that the external data provider did not respond as expected.</span></span>  
  
     <span data-ttu-id="358de-120">다음 예에서는 이러한 로깅 메시지를 포함하는 로그의 예제 행 몇 개를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="358de-120">The following example shows some sample rows from a log that contains these logging messages:</span></span>  
  
    ```  
    ExternalRequest_pre: The object is ready to make the following external request: 'ITransactionJoin::JoinTransaction'.  
    ExternalRequest_post: 'ITransactionJoin::JoinTransaction succeeded'. The external request has completed.  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbConnection.Open'.  
    ExternalRequest_post: 'IDbConnection.Open succeeded'. The external request has completed.  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbConnection.CreateCommand'.  
    ExternalRequest_post: 'IDbConnection.CreateCommand finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbCommand.ExecuteReader'.  
    ExternalRequest_post: 'IDbCommand.ExecuteReader finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDataReader.GetSchemaTable'.  
    ExternalRequest_post: 'IDataReader.GetSchemaTable finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDataReader.Close'.  
    ExternalRequest_post: 'IDataReader.Close finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbConnection.Close'.  
    ExternalRequest_post: 'IDbConnection.Close finished'. The external request has completed."  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="358de-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="358de-121">See Also</span></span>  
 <span data-ttu-id="358de-122">[패키지 배포 문제 해결 도구](troubleshooting-tools-for-package-development.md) </span><span class="sxs-lookup"><span data-stu-id="358de-122">[Troubleshooting Tools for Package Development](troubleshooting-tools-for-package-development.md) </span></span>  
 [<span data-ttu-id="358de-123">패키지 실행 문제 해결 도구</span><span class="sxs-lookup"><span data-stu-id="358de-123">Troubleshooting Tools for Package Execution</span></span>](troubleshooting-tools-for-package-execution.md)  
  
  

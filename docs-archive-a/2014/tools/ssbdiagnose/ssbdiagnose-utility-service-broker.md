---
title: ssbdiagnose 유틸리티(Service Broker) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- Service Broker, runtime reports
- Service Broker, command prompt utilities
- troubleshooting [Service Broker], conversations
- troubleshooting [Service Broker], configurations
- command prompt utilities [Service Broker]
- Service Broker, troubleshooting
- Service Broker, configuration reports
- Service Broker, tools
- troubleshooting [Service Broker], runtime
- conversations [Service Broker], troubleshooting
- troubleshooting [Service Broker], ssbdiagnose utility
- tools [Service Broker], ssbdiagnose
- Service Broker, ssbdiagnose utility
- ssbdiagnose
ms.assetid: 0c1636e8-a3db-438e-be4c-1ea40d1f4877
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8efc581eebd7d8fa7fa265abb54168af78b57ca2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735715"
---
# <a name="ssbdiagnose-utility-service-broker"></a><span data-ttu-id="f05ed-102">ssbdiagnose 유틸리티(Service Broker)</span><span class="sxs-lookup"><span data-stu-id="f05ed-102">ssbdiagnose Utility (Service Broker)</span></span>
  <span data-ttu-id="f05ed-103">**ssbdiagnose** 유틸리티는 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 서비스 구성이나 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 대화의 문제를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-103">The **ssbdiagnose** utility reports issues in [!INCLUDE[ssSB](../../includes/sssb-md.md)] conversations or the configuration of [!INCLUDE[ssSB](../../includes/sssb-md.md)] services.</span></span> <span data-ttu-id="f05ed-104">이때 두 서비스나 한 서비스에 대한 구성 검사를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-104">Configuration checks can be made for either two services or a single service.</span></span> <span data-ttu-id="f05ed-105">오류는 명령 프롬프트 창에 사람이 읽을 수 있는 텍스트 또는 다른 응용 프로그램으로 리디렉션될 수 있는 서식이 설정된 XML로 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-105">Issues are reported either in the command prompt window as human-readable text, or as formatted XML that can be redirected to a file or another program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f05ed-106">구문</span><span class="sxs-lookup"><span data-stu-id="f05ed-106">Syntax</span></span>  
  
```  
  
      ssbdiagnose   
[ [ -XML ]  
    [ -LEVEL { ERROR | WARNING | INFO } ]  
  [-IGNOREerror_id ] [ ...n]  
    [ <baseconnectionoptions> ]  
  { <configurationreport> | <runtimereport> }  
]  
| -?  
  
<configurationreport> ::=  
    CONFIGURATION  
  { [ FROM SERVICEservice_name  
      [ <fromconnectionoptions> ]  
      [ MIRROR <mirrorconnectionoptions> ]  
    ]  
    [ TO SERVICEservice_name[, broker_id ]  
      [ <toconnectionoptions> ]  
      [ MIRROR <mirrorconnectionoptions> ]  
    ]  
  }  
    ON CONTRACTcontract_name  
  [ ENCRYPTION { ON | OFF | ANONYMOUS } ]  
  
<runtime_report> ::=  
    RUNTIME  
    [-SHOWEVENTS ]  
        [ -NEW  
         [ -ID { conversation_handle  
                | conversation_group_id  
                 | conversation_id  
                  }  
        ] [ ...n]  
        ]  
    [ -TIMEOUTtimeout_interval ]  
    [ <runtimeconnectionoptions> ]  
  
<baseconnectionoptions> ::=  
  <connectionoptions>  
  
<fromconnectionoptions> ::=  
  <connectionoptions>  
  
<toconnectionoptions> ::=  
  <connectionoptions>  
  
<mirrorconnectionoptions> ::=  
  <connectionoptions>  
  
<runtimeconnectionoptions> ::=  
  [ CONNECT TO <connectionoptions> ] [ ...n]  
  
<connectionoptions> ::=  
    [ -E | { -Ulogin_id [ -Ppassword ] } ]  
  [ -Sserver_name[\instance_name] ]  
  [ -ddatabase_name ]  
  [ -llogin_timeout ]  
  
```  
  
## <a name="command-line-options"></a><span data-ttu-id="f05ed-107">명령줄 옵션</span><span class="sxs-lookup"><span data-stu-id="f05ed-107">Command Line Options</span></span>  
 <span data-ttu-id="f05ed-108">**-XML**</span><span class="sxs-lookup"><span data-stu-id="f05ed-108">**-XML**</span></span>  
 <span data-ttu-id="f05ed-109">**ssbdiagnose** 출력이 서식이 설정된 XML로 생성되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-109">Specifies that the **ssbdiagnose** output be generated as formatted XML.</span></span> <span data-ttu-id="f05ed-110">이 출력은 파일이나 다른 애플리케이션으로 리디렉션될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-110">This can be redirected to a file or to another application.</span></span> <span data-ttu-id="f05ed-111">**-XML** 을 지정하지 않을 경우 **ssbdiagnose** 출력 형식은 사람이 읽을 수 있는 텍스트로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-111">If **-XML** is not specified, the **ssbdiagnose** output is formatted as human-readable text.</span></span>  
  
 <span data-ttu-id="f05ed-112">**-LEVEL** { **ERROR** | **WARNING** | **INFO**}</span><span class="sxs-lookup"><span data-stu-id="f05ed-112">**-LEVEL** { **ERROR** | **WARNING** | **INFO**}</span></span>  
 <span data-ttu-id="f05ed-113">보고할 메시지 수준을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-113">Specifies the level of messages to report.</span></span>  
  
 <span data-ttu-id="f05ed-114">**ERROR**: 오류 메시지만 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-114">**ERROR**: report only error messages.</span></span>  
  
 <span data-ttu-id="f05ed-115">**WARNING**: 경고 메시지와 오류 메시지를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-115">**WARNING**: report error and warning messages.</span></span>  
  
 <span data-ttu-id="f05ed-116">**INFO**: 오류, 경고 및 정보 메시지를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-116">**INFO**: report error, warning, and informational messages.</span></span>  
  
 <span data-ttu-id="f05ed-117">기본 설정은 **WARNING**입니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-117">The default setting is **WARNING**.</span></span>  
  
 <span data-ttu-id="f05ed-118">**-IGNORE** *error_id*</span><span class="sxs-lookup"><span data-stu-id="f05ed-118">**-IGNORE** *error_id*</span></span>  
 <span data-ttu-id="f05ed-119">지정된 *error_id* 의 오류 또는 메시지가 보고서에 포함되지 않도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-119">Specifies that errors or messages that have the specified *error_id* not be included in reports.</span></span> <span data-ttu-id="f05ed-120">여러 메시지 ID를 표시하지 않으려면 **-IGNORE** 를 여러 번 지정하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-120">You can specify **-IGNORE** multiple times to suppress multiple message IDs.</span></span>  
  
 **\<baseconnectionoptions>**  
 <span data-ttu-id="f05ed-121">특정 절에 연결 옵션이 포함되어 있지 않은 경우 **ssbdiagnose** 에서 사용되는 기본 연결 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-121">Specifies the base connection information that is used by **ssbdiagnose** when connection options are not included in a specific clause.</span></span> <span data-ttu-id="f05ed-122">특정 절에 지정되는 연결 정보는 **baseconnectionoption** 정보보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-122">The connection information that is given in a specific clause overrides the **baseconnectionoption** information.</span></span> <span data-ttu-id="f05ed-123">이 작업은 각 매개 변수에 대해 별도로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-123">This is performed separately for each parameter.</span></span> <span data-ttu-id="f05ed-124">예를 들어 **baseconnetionoptions** 에는 **-S** 와 **-d**가 둘 다 지정되고 **toconnetionoptions** 에는 **-d**만 지정된 경우 **ssbdiagnose** 는 **baseconnetionoptions** 의 -S와 **toconnetionoptions**의 -d를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-124">For example, if both **-S** and **-d** are specified in **baseconnetionoptions**, and only **-d** is specified in **toconnetionoptions**, **ssbdiagnose** uses -S from **baseconnetionoptions** and -d from **toconnetionoptions**.</span></span>  
  
 <span data-ttu-id="f05ed-125">**CONFIGURATION**</span><span class="sxs-lookup"><span data-stu-id="f05ed-125">**CONFIGURATION**</span></span>  
 <span data-ttu-id="f05ed-126">[!INCLUDE[ssSB](../../includes/sssb-md.md)] 서비스 쌍 간 구성 오류 또는 단일 서비스 구성 오류에 대한 보고서를 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-126">Requests a report of configuration errors between a pair of [!INCLUDE[ssSB](../../includes/sssb-md.md)] services, or for a single service.</span></span>  
  
 <span data-ttu-id="f05ed-127">**FROM SERVICE** *service_name*</span><span class="sxs-lookup"><span data-stu-id="f05ed-127">**FROM SERVICE** *service_name*</span></span>  
 <span data-ttu-id="f05ed-128">대화를 시작하는 서비스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-128">Specifies the service that initiates conversations.</span></span>  
  
 **\<fromconnectionoptions>**  
 <span data-ttu-id="f05ed-129">시작자 서비스를 보유하는 데이터베이스에 연결하는 데 필요한 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-129">Specifies the information that is required to connect to the database that holds the initiator service.</span></span> <span data-ttu-id="f05ed-130">**fromconnectionoptions** 를 지정하지 않은 경우 **ssbdiagnose** 는 **baseconnectionoptions** 의 연결 정보를 사용하여 시작자 데이터베이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-130">If **fromconnectionoptions** is not specified, **ssbdiagnose** uses the connection information from **baseconnectionoptions** to connect to the initiator database.</span></span> <span data-ttu-id="f05ed-131">**fromconnectionoptions** 를 지정한 경우 시작자 서비스를 보유하는 데이터베이스를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-131">If **fromconnectionoptions** is specified it must include the database that contains the initiator service.</span></span> <span data-ttu-id="f05ed-132">**fromconnectionoptions** 를 지정하지 않은 경우 **baseconnectionoptions** 에서 시작자 데이터베이스를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-132">If **fromconnectionoptions** is not specified, the **baseconnectionoptions** must specify the initiator database.</span></span>  
  
 <span data-ttu-id="f05ed-133">**TO SERVICE** *service_name*[, *broker_id* ]</span><span class="sxs-lookup"><span data-stu-id="f05ed-133">**TO SERVICE** *service_name*[, *broker_id* ]</span></span>  
 <span data-ttu-id="f05ed-134">대화의 대상이 되는 서비스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-134">Specifies the service that is the target for the conversations.</span></span>  
  
 <span data-ttu-id="f05ed-135">*service_name*: 대상 서비스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-135">*service_name*: specifies the name of the target service.</span></span>  
  
 <span data-ttu-id="f05ed-136">*broker_id*: 대상 데이터베이스를 식별하는 [!INCLUDE[ssSB](../../includes/sssb-md.md)] ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-136">*broker_id*: specifies the [!INCLUDE[ssSB](../../includes/sssb-md.md)] ID that identifies the target database.</span></span> <span data-ttu-id="f05ed-137">*broker_id* 는 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-137">*broker_id* is a GUID.</span></span> <span data-ttu-id="f05ed-138">대상 데이터베이스에서 다음 쿼리를 실행하면 이 ID를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-138">You can run the following query in the target database to find it:</span></span>  
  
```  
SELECT service_broker_guid  
FROM sys.databases  
WHERE database_id = DB_ID();  
```  
  
 **\<toconnectionoptions>**  
 <span data-ttu-id="f05ed-139">대상 서비스를 보유하는 데이터베이스에 연결하는 데 필요한 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-139">Specifies the information that is required to connect the database that holds the target service.</span></span> <span data-ttu-id="f05ed-140">**toconnectionoptions** 를 지정하지 않은 경우 **ssbdiagnose** 는 **baseconnectionoptions** 의 연결 정보를 사용하여 대상 데이터베이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-140">If **toconnectionoptions** is not specified, **ssbdiagnose** uses the connection information from **baseconnectionoptions** to connect to the target database.</span></span>  
  
 <span data-ttu-id="f05ed-141">**MIRROR**</span><span class="sxs-lookup"><span data-stu-id="f05ed-141">**MIRROR**</span></span>  
 <span data-ttu-id="f05ed-142">연결된 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 서비스가 미러된 데이터베이스에서 호스팅되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-142">Specifies that the associated [!INCLUDE[ssSB](../../includes/sssb-md.md)] service is hosted in a mirrored database.</span></span> <span data-ttu-id="f05ed-143">**ssbdiagnose** 는 서비스에 대한 경로가 CREATE ROUTE에 MIRROR_ADDRESS가 지정된 미러된 경로인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-143">**ssbdiagnose** verifies that the route to the service is a mirrored route, where MIRROR_ADDRESS was specified on CREATE ROUTE.</span></span>  
  
 **\<mirrorconnectionoptions>**  
 <span data-ttu-id="f05ed-144">미러 데이터베이스에 연결하는 데 필요한 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-144">Specifies the information that is required to connect to the mirror database.</span></span> <span data-ttu-id="f05ed-145">**mirrorconnectionoptions** 를 지정하지 않은 경우 **ssbdiagnose** 는 **baseconnectionoptions** 의 연결 정보를 사용하여 미러 데이터베이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-145">If **mirrorconnectionoptions** is not specified, **ssbdiagnose** uses the connection information from **baseconnectionoptions** to connect to the mirror database.</span></span>  
  
 <span data-ttu-id="f05ed-146">**ON CONTRACT** *contract_name*</span><span class="sxs-lookup"><span data-stu-id="f05ed-146">**ON CONTRACT** *contract_name*</span></span>  
 <span data-ttu-id="f05ed-147">**ssbdiagnose** 가 지정된 계약을 사용하는 구성만 검사하도록 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-147">Requests that **ssbdiagnose** only check configurations that use the specified contract.</span></span> <span data-ttu-id="f05ed-148">ON CONTRACT를 지정하지 않을 경우 **ssbdiagnose** 는 DEFAULT라는 계약에 대해 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-148">If ON CONTRACT is not specified, **ssbdiagnose** reports on the contract named DEFAULT.</span></span>  
  
 <span data-ttu-id="f05ed-149">**ENCRYPTION** { **ON** | **OFF** | **ANONYMOUS** }</span><span class="sxs-lookup"><span data-stu-id="f05ed-149">**ENCRYPTION** { **ON** | **OFF** | **ANONYMOUS** }</span></span>  
 <span data-ttu-id="f05ed-150">대화가 지정된 수준의 암호화에 대해 올바로 구성되었는지 확인하도록 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-150">Requests verification that the dialog is correctly configured for the specified level of encryption:</span></span>  
  
 <span data-ttu-id="f05ed-151">**ON**: 기본 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-151">**ON**: Default setting.</span></span> <span data-ttu-id="f05ed-152">전체 대화 보안이 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-152">Full dialog security is configured.</span></span> <span data-ttu-id="f05ed-153">인증서가 대화의 양측에 배포되었고, 원격 서비스 바인딩이 있으며, 대상 서비스에 대한 GRANT SEND 문이 시작 사용자를 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-153">Certificates have been deployed on both sides of the dialog, a remote service binding is present, and the GRANT SEND statement for the target service specified the initiator user.</span></span>  
  
 <span data-ttu-id="f05ed-154">**OFF**: 대화 보안이 구성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-154">**OFF**: No dialog security is configured.</span></span> <span data-ttu-id="f05ed-155">인증서가 배포되지 않았고, 원격 서비스 바인딩이 만들어지지 않았으며, 시작자 서비스에 대한 GRANT SEND가 **public** 역할을 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-155">No certificates have been deployed, no remote service binding was created, and the GRANT SEND for the initiator service specified the **public** role.</span></span>  
  
 <span data-ttu-id="f05ed-156">**ANONYMOUS**: 익명 대화 보안이 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-156">**ANONYMOUS**: Anonymous dialog security is configured.</span></span> <span data-ttu-id="f05ed-157">인증서 한 개가 배포되었고, 원격 서비스 바인딩이 익명 절을 지정했으며, 대상 서비스에 대한 GRANT SEND가 **public** 역할을 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-157">One certificate has been deployed, the remote service binding specified the anonymous clause, and the GRANT SEND for the target service specified the **public** role.</span></span>  
  
 <span data-ttu-id="f05ed-158">**RUNTIME**</span><span class="sxs-lookup"><span data-stu-id="f05ed-158">**RUNTIME**</span></span>  
 <span data-ttu-id="f05ed-159">[!INCLUDE[ssSB](../../includes/sssb-md.md)] 대화에 대해 런타임 오류를 일으키는 문제에 대한 보고서를 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-159">Requests a report of issues that cause runtime errors for a [!INCLUDE[ssSB](../../includes/sssb-md.md)] conversation.</span></span> <span data-ttu-id="f05ed-160">**-NEW** 와 **-ID** 를 둘 다 지정하지 않을 경우 **ssbdiagnose** 가 연결 옵션에 지정된 모든 데이터베이스에 있는 대화를 모두 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-160">If neither **-NEW** or **-ID** are specified, **ssbdiagnose** monitors all conversations in all databases specified in the connection options.</span></span> <span data-ttu-id="f05ed-161">**-NEW** 또는 **-ID** 를 지정할 경우 **ssbdiagnose** 는 매개 변수에 지정된 ID 목록을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-161">If **-NEW** or **-ID** are specified, **ssbdiagnose** builds a list of the IDs specified in the parameters.</span></span>  
  
 <span data-ttu-id="f05ed-162">**ssbdiagnose** 는 실행되는 동안 런타임 오류를 나타내는 모든 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 이벤트를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-162">While **ssbdiagnose** is running, it records all [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] events that indicate runtime errors.</span></span> <span data-ttu-id="f05ed-163">즉, 지정된 ID에 대해 발생하는 이벤트뿐 아니라 시스템 수준 이벤트도 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-163">It records the events that occur for the specified IDs, plus system-level events.</span></span> <span data-ttu-id="f05ed-164">런타임 오류가 발생하면 **ssbdiagnose** 는 연결된 구성에 대한 구성 보고서를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-164">If runtime errors are encountered, **ssbdiagnose** runs a configuration report on the associated configuration.</span></span>  
  
 <span data-ttu-id="f05ed-165">기본적으로 출력 보고서에는 런타임 오류가 포함되지 않고 구성 분석 결과만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-165">By default, runtime errors are not included in the output report, only the results of the configuration analysis.</span></span> <span data-ttu-id="f05ed-166">**-SHOWEVENTS** 를 사용하면 보고서에 런타임 오류를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-166">Use **-SHOWEVENTS** to have the runtime errors included in the report.</span></span>  
  
 <span data-ttu-id="f05ed-167">**-SHOWEVENTS**</span><span class="sxs-lookup"><span data-stu-id="f05ed-167">**-SHOWEVENTS**</span></span>  
 <span data-ttu-id="f05ed-168">RUNTIME 보고 동안 **ssbdiagnose** 가 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 이벤트를 보고하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-168">Specifies that **ssbdiagnose** report [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] events during a RUNTIME report.</span></span> <span data-ttu-id="f05ed-169">오류 조건으로 간주되는 이벤트만 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-169">Only events that are considered error conditions are reported.</span></span> <span data-ttu-id="f05ed-170">기본적으로 **ssbdiagnose** 는 오류 이벤트를 모니터링만 하고 출력에 보고하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-170">By default, **ssbdiagnose** only monitors error events; it does not report them in the output.</span></span>  
  
 <span data-ttu-id="f05ed-171">**-NEW**</span><span class="sxs-lookup"><span data-stu-id="f05ed-171">**-NEW**</span></span>  
 <span data-ttu-id="f05ed-172">**ssbdiagnose** 실행 후 시작되는 첫 번째 대화의 런타임 모니터링을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-172">Requests runtime monitoring of the first conversation that begins after **ssbdiagnose** starts running.</span></span>  
  
 <span data-ttu-id="f05ed-173">**-ID**</span><span class="sxs-lookup"><span data-stu-id="f05ed-173">**-ID**</span></span>  
 <span data-ttu-id="f05ed-174">지정된 대화 요소의 런타임 모니터링을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-174">Requests runtime monitoring of the specified conversation elements.</span></span> <span data-ttu-id="f05ed-175">**-ID** 는 여러 번 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-175">You can specify **-ID** multiple times.</span></span>  
  
 <span data-ttu-id="f05ed-176">대화 핸들을 지정할 경우 연결된 대화 엔드포인트와 연결된 이벤트만 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-176">If you specify a conversation handle, only events associated with the associated conversation endpoint are reported.</span></span> <span data-ttu-id="f05ed-177">대화 ID를 지정할 경우 해당 대화와 그 시작자 및 대상 엔드포인트에 대한 이벤트가 모두 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-177">If you specify a conversation ID, all events for that conversation and its initiator and target endpoints are reported.</span></span> <span data-ttu-id="f05ed-178">대화 그룹 ID를 지정할 경우 대화 그룹에 있는 모든 대화와 엔드포인트에 대한 이벤트가 모두 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-178">If a conversation group ID is specified, all events for all conversations and endpoints in the conversation group are reported.</span></span>  
  
 <span data-ttu-id="f05ed-179">*conversation_handle*</span><span class="sxs-lookup"><span data-stu-id="f05ed-179">*conversation_handle*</span></span>  
 <span data-ttu-id="f05ed-180">애플리케이션에 있는 대화 엔드포인트를 식별하는 고유 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-180">A unique identifier that identifies a conversation endpoint in an application.</span></span> <span data-ttu-id="f05ed-181">대화 핸들은 대화의 각 엔드포인트에 고유하기 때문에 시작자 엔드포인트와 대상 엔드포인트는 서로 다른 대화 핸들을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-181">Conversation handles are unique to one endpoint of a conversation, the initiator and target endpoints have separate conversation handles.</span></span>  
  
 <span data-ttu-id="f05ed-182">대화 핸들은 *@dialog_handle* **BEGIN DIALOG** 문의 매개 변수와 `conversation_handle` **RECEIVE** 문의 결과 집합에 있는 열에 의해 응용 프로그램에 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-182">Conversation handles are returned to applications by the *@dialog_handle* parameter of the **BEGIN DIALOG** statement, and the `conversation_handle` column in the result set of a **RECEIVE** statement.</span></span>  
  
 <span data-ttu-id="f05ed-183">대화 핸들은 `conversation_handle` **sys. transmission_queue** 및 **conversation_endpoints** 카탈로그 뷰의 열에 보고 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-183">Conversation handles are reported in the `conversation_handle` column of the **sys.transmission_queue** and **sys.conversation_endpoints** catalog views.</span></span>  
  
 <span data-ttu-id="f05ed-184">*conversation_group_id*</span><span class="sxs-lookup"><span data-stu-id="f05ed-184">*conversation_group_id*</span></span>  
 <span data-ttu-id="f05ed-185">대화 그룹을 식별하는 고유 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-185">The unique identifier that identifies a conversation group.</span></span>  
  
 <span data-ttu-id="f05ed-186">대화 그룹 Id는 *@conversation_group_id* **GET 대화 그룹** 문의 매개 변수와 `conversation_group_id` **RECEIVE** 문의 결과 집합에 있는 열에 의해 응용 프로그램에 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-186">Conversation group IDs are returned to applications by the *@conversation_group_id* parameter of the **GET CONVERSATION GROUP** statement and the `conversation_group_id` column in the result set of a **RECEIVE** statement.</span></span>  
  
 <span data-ttu-id="f05ed-187">대화 그룹 Id는 `conversation_group_id` **sys. conversation_groups** 및 **conversation_endpoints** 카탈로그 뷰의 열에 보고 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-187">Conversation group IDs are reported in the `conversation_group_id` columns of the **sys.conversation_groups** and **sys.conversation_endpoints** catalog views.</span></span>  
  
 <span data-ttu-id="f05ed-188">*conversation_id*</span><span class="sxs-lookup"><span data-stu-id="f05ed-188">*conversation_id*</span></span>  
 <span data-ttu-id="f05ed-189">대화를 식별하는 고유 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-189">The unique identifier that identifies a conversation.</span></span> <span data-ttu-id="f05ed-190">대화의 시작자 엔드포인트와 대상 엔드포인트는 둘 다 동일한 대화 ID를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-190">Conversation IDs are the same for both the initiator and target endpoints of a conversation.</span></span>  
  
 <span data-ttu-id="f05ed-191">대화 Id는 `conversation_id` **sys. conversation_endpoints** 카탈로그 뷰의 열에 보고 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-191">Conversation IDs are reported in the `conversation_id` column of the **sys.conversation_endpoints** catalog view.</span></span>  
  
 <span data-ttu-id="f05ed-192">**-TIMEOUT** *timeout_interval*</span><span class="sxs-lookup"><span data-stu-id="f05ed-192">**-TIMEOUT** *timeout_interval*</span></span>  
 <span data-ttu-id="f05ed-193">**RUNTIME** 보고서를 실행할 시간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-193">Specifies the number of seconds for a **RUNTIME** report to run.</span></span> <span data-ttu-id="f05ed-194">**-TIMEOUT** 을 지정하지 않을 경우 런타임 보고서가 무기한 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-194">If **-TIMEOUT** is not specified the runtime report runs indefinitely.</span></span> <span data-ttu-id="f05ed-195">**-TIMEOUT** 은 **RUNTIME** 보고서에서만 사용됩니다. **CONFIGURATION** 보고서에서는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-195">**-TIMEOUT** is used only on **RUNTIME** reports, not **CONFIGURATION** reports.</span></span> <span data-ttu-id="f05ed-196">Ctrl+C를 사용하면 **-TIMEOUT** 을 지정하지 않은 경우 **ssbdiagnose** 를 종료하거나 제한 시간 간격이 **-** 만료되기 전에 런타임 보고서를 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-196">Use ctrl + C to quit **ssbdiagnose** if **-TIMEOUT** was not specified or to end a runtime report before the time**-** out interval expires.</span></span> <span data-ttu-id="f05ed-197">*timeout_interval* 은 1에서 2,147,483,647 사이의 숫자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-197">*timeout_interval* must be a number between 1 and 2,147,483,647.</span></span>  
  
 **\<runtimeconnectionoptions>**  
 <span data-ttu-id="f05ed-198">모니터링 중인 대화 요소와 연결된 서비스를 포함하는 데이터베이스에 대한 연결 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-198">Specifies the connection information for the databases that contain the services associated with conversation elements being monitored.</span></span> <span data-ttu-id="f05ed-199">모든 서비스가 동일한 데이터베이스에 있으면 **CONNECT TO** 절을 하나만 지정하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-199">If all the services are in the same database, you only have to specify one **CONNECT TO** clause.</span></span> <span data-ttu-id="f05ed-200">서비스가 서로 다른 데이터베이스에 있으면 각 데이터베이스에 대해 **CONNECT TO** 절을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-200">If the services are in separate databases you must supply a **CONNECT TO** clause for each database.</span></span> <span data-ttu-id="f05ed-201">**runtimeconnectionoptions** 를 지정하지 않은 경우 **ssbdiagnose** 는 **baseconnectionoptions**의 연결 정보를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-201">If **runtimeconnectionoptions** is not specified, **ssbdiagnose** uses the connection information from **baseconnectionoptions**.</span></span>  
  
 <span data-ttu-id="f05ed-202">**-E**</span><span class="sxs-lookup"><span data-stu-id="f05ed-202">**-E**</span></span>  
 <span data-ttu-id="f05ed-203">현재 Windows 계정을 로그인 ID로 사용하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 대해 Windows 인증 연결을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-203">Open a Windows Authentication connection to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by using your current Windows account as the login ID.</span></span> <span data-ttu-id="f05ed-204">로그인은 **sysadmin** 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-204">The login must be a member of the **sysadmin** fixed-server role.</span></span>  
  
 <span data-ttu-id="f05ed-205">-E 옵션은 SQLCMDUSER 및 SQLCMDPASSWORD 환경 변수의 사용자와 암호 설정을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-205">The -E option ignores the user and password settings of the SQLCMDUSER and SQLCMDPASSWORD environment variables.</span></span>  
  
 <span data-ttu-id="f05ed-206">**-E** 와 **-U** 를 둘 다 지정하지 않을 경우 **ssbdiagnose** 가 SQLCMDUSER 환경 변수의 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-206">If neither **-E** nor **-U** is specified, **ssbdiagnose** uses the value from the SQLCMDUSER environment variable.</span></span> <span data-ttu-id="f05ed-207">SQLCMDUSER도 설정하지 않을 경우 **ssbdiagnose** 는 Windows 인증을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-207">If SQLCMDUSER is not set either, **ssbdiagnose** uses Windows Authentication.</span></span>  
  
 <span data-ttu-id="f05ed-208">**-E** 옵션과 함께 **-U** 옵션 또는 **-P** 옵션을 사용하면 오류 메시지가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-208">If the **-E** option is used together with the **-U** option or the **-P** option, an error message is generated.</span></span>  
  
 <span data-ttu-id="f05ed-209">**-U** *login_id*</span><span class="sxs-lookup"><span data-stu-id="f05ed-209">**-U** *login_id*</span></span>  
 <span data-ttu-id="f05ed-210">지정된 로그인 ID를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증 연결을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-210">Open a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication connection by using the specified login ID.</span></span> <span data-ttu-id="f05ed-211">로그인은 **sysadmin** 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-211">The login must be a member of the **sysadmin** fixed-server role.</span></span>  
  
 <span data-ttu-id="f05ed-212">**-E** 와 **-U** 를 둘 다 지정하지 않을 경우 **ssbdiagnose** 가 SQLCMDUSER 환경 변수의 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-212">If neither **-E** nor **-U** is specified, **ssbdiagnose** uses the value from the SQLCMDUSER environment variable.</span></span> <span data-ttu-id="f05ed-213">SQLCMDUSER도 설정하지 않을 경우 **ssbdiagnose** 는 **ssbdiagnose**를 실행하는 사용자의 Windows 계정을 기반으로 하는 Windows 인증 모드를 사용하여 연결을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-213">If SQLCMDUSER is not set either, **ssbdiagnose** tries to connect by using Windows Authentication mode based on the Windows account of the user who is running **ssbdiagnose**.</span></span>  
  
 <span data-ttu-id="f05ed-214">**-U** 옵션과 함께 **-E** 옵션을 사용하면 오류 메시지가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-214">If the **-U** option is used together with the **-E** option, an error message is generated.</span></span> <span data-ttu-id="f05ed-215">**–U** 옵션 다음에 둘 이상의 인수를 지정하면 오류 메시지가 생성되고 프로그램이 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-215">If the **-U** option is followed by more than one argument, an error message is generated and the program exits.</span></span>  
  
 <span data-ttu-id="f05ed-216">**-P** *password*</span><span class="sxs-lookup"><span data-stu-id="f05ed-216">**-P** *password*</span></span>  
 <span data-ttu-id="f05ed-217">**-U** 로그인 ID의 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-217">Specifies the password for the **-U** login ID.</span></span> <span data-ttu-id="f05ed-218">암호는 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-218">Passwords are case sensitive.</span></span> <span data-ttu-id="f05ed-219">**-U** 옵션만 사용하고 **-P** 옵션을 사용하지 않을 경우 **ssbdiagnose** 는 SQLCMDPASSWORD 환경 변수의 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-219">If the **-U** option is used and the **-P** option is not used, **ssbdiagnose** uses the value from the SQLCMDPASSWORD environment variable.</span></span> <span data-ttu-id="f05ed-220">SQLCMDPASSWORD도 설정하지 않을 경우 **ssbdiagnose** 는 사용자에게 암호를 묻는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-220">If SQLCMDPASSWORD is not set either, **ssbdiagnose** prompts the user for a password.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f05ed-221">SET SQLCMDPASSWORD 명령을 입력하면 모니터에서 누구나 암호를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-221">When you type a SET SQLCMDPASSWORD command, your password will be visible to anyone who can see your monitor.</span></span>  
  
 <span data-ttu-id="f05ed-222">**-P** 옵션을 암호 없이 지정할 경우 **ssbdiagnose** 는 기본 암호(NULL)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-222">If the **-P** option is specified without a password **ssbdiagnose** uses the default password (NULL).</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] <span data-ttu-id="f05ed-223">자세한 내용은 [강력한 암호](../../relational-databases/security/strong-passwords.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f05ed-223">For more information, see [Strong Passwords](../../relational-databases/security/strong-passwords.md).</span></span>  
  
 <span data-ttu-id="f05ed-224">암호 프롬프트는 다음과 같이 콘솔에 출력되어 표시됩니다. `Password:`</span><span class="sxs-lookup"><span data-stu-id="f05ed-224">The password prompt is displayed by printing the password prompt to the console, as follows: `Password:`</span></span>  
  
 <span data-ttu-id="f05ed-225">사용자 입력은 숨겨지므로</span><span class="sxs-lookup"><span data-stu-id="f05ed-225">User input is hidden.</span></span> <span data-ttu-id="f05ed-226">아무 것도 표시되지 않고 커서가 해당 위치에 그대로 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-226">This means that nothing is displayed and the cursor stays in position.</span></span>  
  
 <span data-ttu-id="f05ed-227">**-P** 옵션과 함께 **-E** 옵션을 사용하면 오류 메시지가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-227">If the **-P** option is used with the **-E** option, an error message is generated.</span></span>  
  
 <span data-ttu-id="f05ed-228">**-P** 옵션 다음에 둘 이상의 인수를 지정하면 오류 메시지가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-228">If the **-P** option is followed by more than one argument, an error message is generated.</span></span>  
  
 <span data-ttu-id="f05ed-229">**-S** *server_name*[\\*instance_name*]</span><span class="sxs-lookup"><span data-stu-id="f05ed-229">**-S** *server_name*[\\*instance_name*]</span></span>  
 <span data-ttu-id="f05ed-230">분석할 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 서비스를 보유하는 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-230">Specifies the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that holds the [!INCLUDE[ssSB](../../includes/sssb-md.md)] services to be analyzed.</span></span>  
  
 <span data-ttu-id="f05ed-231">해당 서버에 있는 기본 *인스턴스에 연결하려면* server_name [!INCLUDE[ssDE](../../includes/ssde-md.md)] 을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-231">Specify *server_name* to connect to the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on that server.</span></span> <span data-ttu-id="f05ed-232">해당 서버에 있는의 명명 된 인스턴스에 연결 하려면 *server_name ***\\*** instance_name* 를 지정 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-232">Specify *server_name***\\***instance_name* to connect to a named instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on that server.</span></span> <span data-ttu-id="f05ed-233">**-S** 를 지정하지 않으면 **ssbdiagnose** 가 기본적으로 SQLCMDSERVER 환경 변수의 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-233">If **-S** is not specified, **ssbdiagnose** uses the value of the SQLCMDSERVER environment variable.</span></span> <span data-ttu-id="f05ed-234">SQLCMDSERVER도 설정하지 않을 경우 **ssbdiagnose** 는 로컬 컴퓨터에 있는 기본 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-234">If SQLCMDSERVER is not set either, **ssbdiagnose** connects to the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on the local computer.</span></span>  
  
 <span data-ttu-id="f05ed-235">**-d** *database_name*</span><span class="sxs-lookup"><span data-stu-id="f05ed-235">**-d** *database_name*</span></span>  
 <span data-ttu-id="f05ed-236">분석할 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 서비스를 보유하는 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-236">Specifies the database that holds the [!INCLUDE[ssSB](../../includes/sssb-md.md)] services to be analyzed.</span></span> <span data-ttu-id="f05ed-237">데이터베이스가 없을 경우에는 오류가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-237">If the database does not exist, an error message is generated.</span></span> <span data-ttu-id="f05ed-238">**-d** 를 지정하지 않을 경우 기본적으로 로그인의 기본 데이터베이스 속성에 지정된 데이터베이스가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-238">If **-d** is not specified, the default is the database specified in the default-database property for your login.</span></span>  
  
 <span data-ttu-id="f05ed-239">**-l** *login_timeout*</span><span class="sxs-lookup"><span data-stu-id="f05ed-239">**-l** *login_timeout*</span></span>  
 <span data-ttu-id="f05ed-240">서버 연결 시도 시간이 초과되기 전의 대기 시간을 초 단위로 지정합니다. **-l** 를 지정하지 않을 경우 **ssbdiagnose** 가 SQLCMDLOGINTIMEOUT 환경 변수의 값 집합을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-240">Specifies the number of seconds before an attempt to connect to a server times out. If **-l** is not specified, **ssbdiagnose** uses the value set for the SQLCMDLOGINTIMEOUT environment variable.</span></span> <span data-ttu-id="f05ed-241">SQLCMDLOGINTIMEOUT도 설정하지 않을 경우 기본 제한 시간은 30초입니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-241">If SQLCMDLOGINTIMEOUT is not set either, the default time-out is thirty seconds.</span></span> <span data-ttu-id="f05ed-242">로그인 제한 시간은 0에서 65534 사이의 숫자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-242">The login time-out must be a number between 0 and 65534.</span></span> <span data-ttu-id="f05ed-243">입력한 값이 숫자가 아니거나 이 범위에 속하지 않을 경우 **ssbdiagnose** 는 오류 메시지를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-243">If the value that is supplied is not numeric or does not fall into that range, **ssbdiagnose** generates an error message.</span></span> <span data-ttu-id="f05ed-244">값을 0으로 설정하면 제한 시간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-244">A value of 0 specifies time-out to be infinite.</span></span>  
  
 <span data-ttu-id="f05ed-245">**-?**</span><span class="sxs-lookup"><span data-stu-id="f05ed-245">**-?**</span></span>  
 <span data-ttu-id="f05ed-246">명령줄 도움말을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-246">Displays command line help.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f05ed-247">설명</span><span class="sxs-lookup"><span data-stu-id="f05ed-247">Remarks</span></span>  
 <span data-ttu-id="f05ed-248">**ssbdiagnose** 를 사용하여 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-248">Use **ssbdiagnose** to do the following:</span></span>  
  
-   <span data-ttu-id="f05ed-249">새로 구성된 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 애플리케이션에 구성 오류가 없음을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-249">Confirm that there are no configuration errors in a newly configured [!INCLUDE[ssSB](../../includes/sssb-md.md)] application.</span></span>  
  
-   <span data-ttu-id="f05ed-250">기존 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 애플리케이션의 구성을 변경한 후에 구성 오류가 없음을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-250">Confirm that there are no configuration errors after changing the configuration of an existing [!INCLUDE[ssSB](../../includes/sssb-md.md)] application.</span></span>  
  
-   <span data-ttu-id="f05ed-251">[!INCLUDE[ssSB](../../includes/sssb-md.md)] 데이터베이스가 분리된 다음 새 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 다시 연결된 후에 구성 오류가 없음을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-251">Confirm that there are no configuration errors after a [!INCLUDE[ssSB](../../includes/sssb-md.md)] database is detached and then reattached to a new instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="f05ed-252">서비스 간에 메시지가 성공적으로 전송되지 않은 경우 구성 오류가 있는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-252">Research whether there are configuration errors when messages are not successfully transmitted between services.</span></span>  
  
-   <span data-ttu-id="f05ed-253">[!INCLUDE[ssSB](../../includes/sssb-md.md)] 대화 요소 집합에서 발생하는 모든 오류에 대한 보고서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-253">Get a report of any errors that occur in a set of [!INCLUDE[ssSB](../../includes/sssb-md.md)] conversation elements.</span></span>  
  
## <a name="configuration-reporting"></a><span data-ttu-id="f05ed-254">구성 보고</span><span class="sxs-lookup"><span data-stu-id="f05ed-254">Configuration Reporting</span></span>  
 <span data-ttu-id="f05ed-255">대화에 사용되는 구성을 올바로 분석하려면 대화에 사용되는 것과 동일한 옵션을 사용하는 **ssbdiagnose** 구성 보고서를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-255">To correctly analyze the configuration used by a conversation, run a **ssbdiagnose** configuration report that uses the same options that are used by the conversation.</span></span> <span data-ttu-id="f05ed-256">대화에 사용되는 것보다 낮은 수준의 옵션을 **ssbdiagnose** 에 지정할 경우 **ssbdiagnose** 가 대화에 필요한 조건을 보고하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-256">If you specify a lower level of options for **ssbdiagnose** than are used by the conversation, **ssbdiagnose** might not report conditions that are required by the conversation.</span></span> <span data-ttu-id="f05ed-257">대화에 사용되는 것보다 높은 수준의 옵션을 **ssbdiagnose**에 지정할 경우 대화에 필요하지 않은 항목을 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-257">If you specify a higher level of options for **ssbdiagnose**, it might report items that are not required by the conversation.</span></span> <span data-ttu-id="f05ed-258">예를 들어 동일한 데이터베이스에 있는 두 서비스 간의 대화가 ENCPRYPTION이 OFF인 상태에서 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-258">For example, a conversation between two services in the same database can be run with ENCPRYPTION OFF.</span></span> <span data-ttu-id="f05ed-259">**ssbdiagnose** 를 실행하여 두 서비스 간 구성의 유효성을 검사하는 경우 기본 ENCRYPTION ON 설정을 사용하면 **ssbdiagnose** 가 데이터베이스에 마스터 키가 없음을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-259">If you run **ssbdiagnose** to validate the configuration between the two services, but use the default ENCRYPTION ON setting, **ssbdiagnose** reports that the database is missing a master key.</span></span> <span data-ttu-id="f05ed-260">마스터 키는 대화에 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-260">A master key is not required for the conversation.</span></span>  
  
 <span data-ttu-id="f05ed-261">**ssbdiagnose** 구성 보고서는 실행될 때마다 하나 또는 한 쌍의 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 서비스만 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-261">The **ssbdiagnose** configuration report analyzes only one [!INCLUDE[ssSB](../../includes/sssb-md.md)] service or a single pair of services every time it is run.</span></span> <span data-ttu-id="f05ed-262">여러 쌍의 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 서비스를 보고하려면 **ssbdiagnose** 를 여러 번 호출하는 .cmd 명령 파일을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-262">To report on multiple pairs of [!INCLUDE[ssSB](../../includes/sssb-md.md)] services, build a .cmd command file that calls **ssbdiagnose** multiple times.</span></span>  
  
## <a name="runtime-reporting"></a><span data-ttu-id="f05ed-263">런타임 보고</span><span class="sxs-lookup"><span data-stu-id="f05ed-263">Runtime Reporting</span></span>  
 <span data-ttu-id="f05ed-264">-RUNTIME을 지정할 경우 **ssbdiagnose** 는 **runtimeconnectionoptions** 및 **baseconnectionoptions** 에 지정된 모든 데이터베이스를 검색하여 [!INCLUDE[ssSB](../../includes/sssb-md.md)] ID 목록을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-264">When -RUNTIME is specified, **ssbdiagnose** searches all databases specified in **runtimeconnectionoptions** and **baseconnectionoptions** to build a list of [!INCLUDE[ssSB](../../includes/sssb-md.md)] IDs.</span></span> <span data-ttu-id="f05ed-265">작성되는 전체 ID 목록은 다음과 같이 -NEW 및 -ID가 어떻게 지정되는지에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-265">The full list of IDs built depends on what is specified for -NEW and -ID:</span></span>  
  
-   <span data-ttu-id="f05ed-266">**-NEW** 와 **-ID** 를 둘 다 지정하지 않을 경우 목록에 연결 옵션에 지정된 모든 데이터베이스에 있는 대화가 모두 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-266">If neither **-NEW** or **-ID** are specified, the list includes all conversations for all databases specified in the connection options.</span></span>  
  
-   <span data-ttu-id="f05ed-267">**-NEW** 를 지정할 경우 **ssbdiagnose** 는 **ssbdiagnose** 가 실행된 후 시작되는 첫 번째 대화의 요소를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-267">If **-NEW** is specified, **ssbdiagnose** includes the elements for the first conversation that starts after **ssbdiagnose** is run.</span></span> <span data-ttu-id="f05ed-268">여기에는 대상 대화 엔드포인트와 시작자 대화 엔드포인트 둘 다에 대한 대화 ID와 대화 핸들이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-268">This includes the conversation ID and the conversation handles for both the target and initiator conversation endpoints.</span></span>  
  
-   <span data-ttu-id="f05ed-269">대화 핸들을 사용하여 **-ID** 가 지정된 경우에는 해당 핸들만 목록에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-269">If **-ID** is specified with a conversation handle, only that handle is included in the list.</span></span>  
  
-   <span data-ttu-id="f05ed-270">대화 ID를 사용하여 **-ID** 가 지정된 경우에는 두 대화 엔드포인트 모두에 대한 대화 ID와 핸들이 목록에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-270">If **-ID** is specified with a conversation ID, the conversation ID and the handles for both of its conversation endpoints are added to the list.</span></span>  
  
-   <span data-ttu-id="f05ed-271">대화 그룹 ID를 사용하여 **-ID** 가 지정된 경우에는 그룹에 있는 모든 대화 ID와 대화 핸들이 목록에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-271">If **-ID** is specified with a conversation group ID, all the conversation IDs and conversation handles in that group are added to the list.</span></span>  
  
 <span data-ttu-id="f05ed-272">연결 옵션에 지정되지 않은 데이터베이스의 요소는 목록에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-272">The list does not include elements from databases that are not covered by the connection options.</span></span> <span data-ttu-id="f05ed-273">예를 들어 **-ID** 를 사용하여 대화 ID를 지정할 때 시작자 데이터베이스에 대해서만 **runtimeconnectionoptions** 절을 제공하고 대상 데이터베이스에 대해서는 제공하지 않을 경우</span><span class="sxs-lookup"><span data-stu-id="f05ed-273">For example, assume that you use **-ID** to specify a conversation ID, but only provide a **runtimeconnectionoptions** clause for the initiator database and not the target database.</span></span> <span data-ttu-id="f05ed-274">**ssbdiagnose** 는 해당 ID 목록에 대화 ID와 시작자 대화 핸들만 포함하고 대상 대화 핸들을 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-274">**ssbdiagnose** will not include the target conversation handle in its list of IDs, only the conversation ID and the initiator conversation handle.</span></span>  
  
 <span data-ttu-id="f05ed-275">**ssbdiagnose** 모니터는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] runtimeconnectionoptions **및** baseconnectionoptions **에 지정된 데이터베이스에서**이벤트를 모니터링하며,</span><span class="sxs-lookup"><span data-stu-id="f05ed-275">**ssbdiagnose** monitors the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] events from the databases covered by **runtimeconnectionoptions** and **baseconnectionoptions**.</span></span> <span data-ttu-id="f05ed-276">런타임 목록에 있는 하나 이상의 [!INCLUDE[ssSB](../../includes/sssb-md.md)] ID에서 오류가 발생했음을 나타내는 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 이벤트를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-276">It searches for [!INCLUDE[ssSB](../../includes/sssb-md.md)] events that indicate an error was encountered by one or more of the [!INCLUDE[ssSB](../../includes/sssb-md.md)] IDs in the runtime list.</span></span> <span data-ttu-id="f05ed-277">또한**ssbdiagnose** 는 특별히 대화 그룹과 연관이 없는 시스템 수준 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 오류 이벤트를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-277">**ssbdiagnose** also searches for system-level [!INCLUDE[ssSB](../../includes/sssb-md.md)] error events not specifically associated with any conversation group.</span></span>  
  
 <span data-ttu-id="f05ed-278">**ssbdiagnose** 는 대화 오류를 찾을 경우 구성 보고서를 추가로 실행하여 해당 이벤트의 근본 원인을 보고하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-278">If **ssbdiagnose** finds conversation errors, the utility will attempt to report on the root cause of the events by also running a configuration report.</span></span> <span data-ttu-id="f05ed-279">**ssbdiagnose** 는 데이터베이스의 메타데이터를 사용하여 해당 대화에 사용된 인스턴스, [!INCLUDE[ssSB](../../includes/sssb-md.md)] ID, 데이터베이스, 서비스 및 계약을 파악한 다음</span><span class="sxs-lookup"><span data-stu-id="f05ed-279">**ssbdiagnose** uses the metadata in the databases to try to determine the instances, [!INCLUDE[ssSB](../../includes/sssb-md.md)] IDs, databases, services, and contracts used by the conversation.</span></span> <span data-ttu-id="f05ed-280">사용 가능한 모든 정보를 사용하여 구성 보고서를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-280">It then runs a configuration report using all available information.</span></span>  
  
 <span data-ttu-id="f05ed-281">기본적으로 **ssbdiagnose** 는 오류 이벤트를 보고하지 않고</span><span class="sxs-lookup"><span data-stu-id="f05ed-281">By default, **ssbdiagnose** does not report error events.</span></span> <span data-ttu-id="f05ed-282">구성 검사 동안 발견된 기본 문제만 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-282">It only reports the underlying issues found during the configuration check.</span></span> <span data-ttu-id="f05ed-283">따라서 보고되는 정보량이 최소화되고 기본 구성 문제에 집중하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-283">This minimizes the amount of information reported and helps you focus on the underlying configuration issues.</span></span> <span data-ttu-id="f05ed-284">**-SHOWEVENTS** 를 지정할 경우 **ssbdiagnose**에서 발생한 오류 이벤트를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-284">You can specify **-SHOWEVENTS** to see the error events encountered by **ssbdiagnose**.</span></span>  
  
## <a name="issues-reported-by-ssbdiagnose"></a><span data-ttu-id="f05ed-285">ssbdiagnose가 보고하는 문제</span><span class="sxs-lookup"><span data-stu-id="f05ed-285">Issues Reported by ssbdiagnose</span></span>  
 <span data-ttu-id="f05ed-286">**ssbdiagnose** 는 세 가지 문제 클래스를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-286">**ssbdiagnose** reports three classes of issues.</span></span> <span data-ttu-id="f05ed-287">XML 출력 파일에서 각 문제 클래스는 서로 다른 유형의 Issue 요소로 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-287">In the XML output file, each class of issue is reported as a separate type of the Issue element.</span></span> <span data-ttu-id="f05ed-288">**ssbdiagnose** 가 보고하는 이러한 세 가지 유형의 문제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-288">The three types of issues reported by **ssbdiagnose** are as follows:</span></span>  
  
 <span data-ttu-id="f05ed-289">**진단**</span><span class="sxs-lookup"><span data-stu-id="f05ed-289">**Diagnosis**</span></span>  
 <span data-ttu-id="f05ed-290">구성 문제를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-290">Reports a configuration issue.</span></span> <span data-ttu-id="f05ed-291">여기에는 **CONFIGURATION** 보고서가 실행되는 동안이나 **RUNTIME** 보고서의 구성 단계에서 발견된 문제가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-291">This includes issues found either a **CONFIGURATION** report is running, or during the configuration phase of a **RUNTIME** report.</span></span> <span data-ttu-id="f05ed-292">**ssbdiagnose** 는 한 번에 하나의 구성 문제를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-292">**ssbdiagnose** reports each configuration issue one time.</span></span>  
  
 <span data-ttu-id="f05ed-293">**이벤트**</span><span class="sxs-lookup"><span data-stu-id="f05ed-293">**Event**</span></span>  
 <span data-ttu-id="f05ed-294">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] RUNTIME **보고 동안 모니터링 중인 대화에서 문제가 발생했음을 나타내는** 이벤트를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-294">Reports a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] event that indicates a problem was encountered by a conversation being monitored during a **RUNTIME** report.</span></span> <span data-ttu-id="f05ed-295">**ssbdiagnose** 는 이벤트가 발생할 때마다 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-295">**ssbdiagnose** reports events every time they are generated.</span></span> <span data-ttu-id="f05ed-296">따라서 여러 대화에서 문제가 발생할 경우 이벤트가 여러 번 보고될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-296">Events can be reported multiple times if several conversations encounter the problem.</span></span>  
  
 <span data-ttu-id="f05ed-297">**문제**</span><span class="sxs-lookup"><span data-stu-id="f05ed-297">**Problem**</span></span>  
 <span data-ttu-id="f05ed-298">**ssbdiagnose** 가 구성 분석을 완료하거나 대화를 모니터링하지 못하게 하는 문제를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-298">Reports an issue that is preventing **ssbdiagnose** from completing a configuration analysis or from monitoring conversations.</span></span>  
  
## <a name="sqlcmd-environment-variables"></a><span data-ttu-id="f05ed-299">sqlcmd 환경 변수</span><span class="sxs-lookup"><span data-stu-id="f05ed-299">sqlcmd Environment Variables</span></span>  
 <span data-ttu-id="f05ed-300">**ssbdiagnose** 유틸리티는 **sqlcmd** 유틸리티도 사용하는 SQLCMDSERVER, SQLCMDUSER, SQLCMDPASSWORD 및 SQLCMDLOGINTIMOUT 환경 변수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-300">The **ssbdiagnose** utility supports the SQLCMDSERVER, SQLCMDUSER, SQLCMDPASSWORD, and SQLCMDLOGINTIMOUT environment variables that are also used by the **sqlcmd** utility.</span></span> <span data-ttu-id="f05ed-301">환경 변수는 명령 프롬프트 SET 명령을 사용하여 설정하거나 **sqlcmd** 를 사용하여 실행하는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트에서 **setvar**명령을 사용하여 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-301">You can set the environment variables either by using the command prompt SET command, or by using the **setvar** command in [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts that you run by using **sqlcmd**.</span></span> <span data-ttu-id="f05ed-302">**sqlcmd** 에서 **setvar**을 사용하는 방법은 [스크립팅 변수와 함께 sqlcmd 사용](../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f05ed-302">For more information about how to use **setvar** in **sqlcmd**, see [Use sqlcmd with Scripting Variables](../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md).</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="f05ed-303">사용 권한</span><span class="sxs-lookup"><span data-stu-id="f05ed-303">Permissions</span></span>  
 <span data-ttu-id="f05ed-304">각 **connectionoptions** 절에서 **-E** 또는 **-U** 를 사용하여 지정된 로그인은 **-S** 에 지정된 인스턴스에 있는 **sysadmin**고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-304">In each **connectionoptions** clause, the login specified with either **-E** or **-U** must be a member of the **sysadmin** fixed-server role in the instance specified in **-S**.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="f05ed-305">예</span><span class="sxs-lookup"><span data-stu-id="f05ed-305">Examples</span></span>  
 <span data-ttu-id="f05ed-306">이 섹션에는 명령 프롬프트에서 **ssbdiagnose** 를 사용하는 예가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-306">This section contains examples of using **ssbdiagnose** at a command prompt.</span></span>  
  
### <a name="a-checking-the-configuration-of-two-services-in-the-same-database"></a><span data-ttu-id="f05ed-307">A.</span><span class="sxs-lookup"><span data-stu-id="f05ed-307">A.</span></span> <span data-ttu-id="f05ed-308">동일한 데이터베이스에 있는 두 서비스의 구성 검사</span><span class="sxs-lookup"><span data-stu-id="f05ed-308">Checking the Configuration of Two Services in the Same Database</span></span>  
 <span data-ttu-id="f05ed-309">다음 예에서는 아래 조건에 해당하는 경우 구성 보고서를 요청하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-309">The following example shows how to request a configuration report when the following are true;</span></span>  
  
-   <span data-ttu-id="f05ed-310">시작자 서비스와 대상 서비스가 동일한 데이터베이스에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-310">The initiator and target service are in the same database.</span></span>  
  
-   <span data-ttu-id="f05ed-311">데이터베이스가 기본 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-311">The database is in the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="f05ed-312">인스턴스가 **ssbdiagnose** 가 실행되는 동일한 컴퓨터에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-312">The instances is on the same computer on which **ssbdiagnose** is run.</span></span>  
  
 <span data-ttu-id="f05ed-313">**ssbdiagnose** 유틸리티는 ON CONTRACT가 지정되지 않았기 때문에 DEFAULT 계약을 사용하는 구성을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-313">The **ssbdiagnose** utility reports the configuration that uses the DEFAULT contract because ON CONTRACT is not specified.</span></span>  
  
```  
ssbdiagnose -E -d MyDatabase CONFIGURATION FROM SERVICE /test/initiator TO SERVICE /test/target  
```  
  
### <a name="b-checking-the-configuration-of-two-services-on-separate-computers-that-use-one-login"></a><span data-ttu-id="f05ed-314">B.</span><span class="sxs-lookup"><span data-stu-id="f05ed-314">B.</span></span> <span data-ttu-id="f05ed-315">별개의 컴퓨터에 있지만 동일한 로그인을 사용하는 두 서비스의 구성 검사</span><span class="sxs-lookup"><span data-stu-id="f05ed-315">Checking the Configuration of Two Services on Separate Computers That Use One Login</span></span>  
 <span data-ttu-id="f05ed-316">다음 예에서는 시작자 서비스와 대상 서비스가 서로 다른 컴퓨터에 있지만 동일한 Windows 인증 로그인을 사용하여 액세스할 수 있는 경우 구성 보고서를 요청하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-316">The following example shows how to request a configuration report when the initiator and target service are on separate computers, but can be accessed by using the same Windows Authentication login.</span></span>  
  
```  
ssbdiagnose -E CONFIGURATION FROM SERVICE /text/initiator -S InitiatorComputer -d InitiatorDatabase TO SERVICE /test/target -S TargetComputer -d TargetDatabase ON CONTRACT TestContract  
```  
  
### <a name="c-checking-the-configuration-of-two-services-on-separate-computers-that-use-separate-logins"></a><span data-ttu-id="f05ed-317">C.</span><span class="sxs-lookup"><span data-stu-id="f05ed-317">C.</span></span> <span data-ttu-id="f05ed-318">별개의 컴퓨터에 있으며 서로 다른 로그인을 사용하는 두 서비스의 구성 검사</span><span class="sxs-lookup"><span data-stu-id="f05ed-318">Checking the Configuration of Two Services on Separate Computers That Use Separate Logins</span></span>  
 <span data-ttu-id="f05ed-319">다음 예에서는 시작자 서비스와 대상 서비스가 서로 다른 컴퓨터에 있고 각 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대해 서로 다른 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인증 로그인이 필요한 경우 구성 보고서를 요청하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-319">The following example shows how to request a configuration report when the initiator and target service are on separate computers, and separate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication logins are required for each instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
```  
ssbdiagnose CONFIGURATION FROM SERVICE /text/initiator   
-S InitiatorComputer -U InitiatorLogin -p !wEx23Dvb   
-d InitiatorDatabase TO SERVICE /test/target -S TargetComputer   
-U TargetLogin -p ER!49jiy -d TargetDatabase ON CONTRACT TestContract  
```  
  
### <a name="d-checking-mirrored-service-configurations-on-separate-computers-with-anonymous-encryption"></a><span data-ttu-id="f05ed-320">D.</span><span class="sxs-lookup"><span data-stu-id="f05ed-320">D.</span></span> <span data-ttu-id="f05ed-321">익명 암호화를 사용하는 서로 다른 컴퓨터에 있는 미러된 서비스 구성 검사</span><span class="sxs-lookup"><span data-stu-id="f05ed-321">Checking Mirrored Service Configurations on Separate Computers With Anonymous Encryption</span></span>  
 <span data-ttu-id="f05ed-322">다음 예에서는 시작자 서비스와 대상 서비스가 서로 다른 컴퓨터에 있고 시작자가 명명된 인스턴스에 미러된 경우 보고서를 요청하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-322">The following example shows how to request a configuration report when the initiator and target service are on separate computers and the initiator is mirrored to a named instance.</span></span> <span data-ttu-id="f05ed-323">보고서는 서비스가 익명 암호화를 사용하도록 구성되어 있는지도 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-323">The report also verifies that the services are configured to use anonymous encryption.</span></span>  
  
```  
ssbdiagnose -E CONFIGURATION FROM SERVICE /text/initiator   
-S InitiatorComputer -d InitiatorDatabase MIRROR   
-S MirrorComputer/MirrorInstance TO SERVICE /test/target   
-S TargetComputer -d TargetDatabase ON CONTRACT TestContract ENCRYPTION ANONYMOUS  
```  
  
### <a name="e-checking-the-configuration-of-two-contracts"></a><span data-ttu-id="f05ed-324">E.</span><span class="sxs-lookup"><span data-stu-id="f05ed-324">E.</span></span> <span data-ttu-id="f05ed-325">두 계약의 구성 검사</span><span class="sxs-lookup"><span data-stu-id="f05ed-325">Checking the Configuration of Two Contracts</span></span>  
 <span data-ttu-id="f05ed-326">다음 예에서는 아래 조건에 해당하는 경우 구성 보고서를 요청하는 명령 파일을 작성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-326">The following example shows how to build a command file that requests configuration reports when the following are true:</span></span>  
  
-   <span data-ttu-id="f05ed-327">시작자 서비스와 대상 서비스가 동일한 데이터베이스에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-327">The initiator and target service are in the same database.</span></span>  
  
-   <span data-ttu-id="f05ed-328">데이터베이스가 기본 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-328">The database is in the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="f05ed-329">인스턴스가 **ssbdiagnose** 가 실행되는 동일한 컴퓨터에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-329">The instance is on the same computer on which **ssbdiagnose** is run.</span></span>  
  
 <span data-ttu-id="f05ed-330">**ssbdiagnose** 유틸리티는 실행될 때마다 동일한 서비스 간에 서로 다른 계약을 사용하는 구성을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-330">Each time **ssbdiagnose** is run it reports the configuration for a different contract between the same services.</span></span>  
  
```  
ssbdiagnose -E -d MyDatabase CONFIGURATION FROM SERVICE   
/test/initiator TO SERVICE /test/target ON CONTRACT PayRaiseContract  
ssbdiagnose -E -d MyDatabase CONFIGURATION FROM SERVICE /test/initiator   
TO SERVICE /test/target ON CONTRACT PromotionContract  
```  
  
### <a name="f-monitor-the-status-of-a-specific-conversation-on-the-local-computer-with-a-time-out"></a><span data-ttu-id="f05ed-331">F.</span><span class="sxs-lookup"><span data-stu-id="f05ed-331">F.</span></span> <span data-ttu-id="f05ed-332">제한 시간이 설정된 로컬 컴퓨터에 있는 특정 대화 상태 모니터링</span><span class="sxs-lookup"><span data-stu-id="f05ed-332">Monitor the status of a specific conversation on the local computer with a time out</span></span>  
 <span data-ttu-id="f05ed-333">다음 예에서는 시작자 서비스와 대상 서비스가 **ssbdiagnose**를 실행하고 있는 동일한 컴퓨터의 기본 인스턴스에 있는 동일한 데이터베이스에 있는 특정 대화를 모니터링하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-333">The following example shows how to monitor a specific conversation where the initiator and target services are in the same database in the default instance of the same computer that is running **ssbdiagnose**.</span></span> <span data-ttu-id="f05ed-334">제한 시간 간격은 20초로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-334">The time-out interval is set to 20 seconds.</span></span>  
  
```  
ssbdiagnose -E -d TestDatabase RUNTIME -ID D68D77A9-B1CF-41BF-A5CE-279ABCAB140D -TIMEOUT 20  
```  
  
### <a name="g-monitor-the-status-of-a-conversation-that-spans-two-computers"></a><span data-ttu-id="f05ed-335">G.</span><span class="sxs-lookup"><span data-stu-id="f05ed-335">G.</span></span> <span data-ttu-id="f05ed-336">두 컴퓨터를 연결하는 대화의 상태 모니터링</span><span class="sxs-lookup"><span data-stu-id="f05ed-336">Monitor the status of a conversation that spans two computers</span></span>  
 <span data-ttu-id="f05ed-337">다음 예에서는 시작자 서비스와 대상 서비스가 서로 다른 컴퓨터에 있는 특정 대화를 모니터링하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-337">The following example shows how to monitor a specific conversation where the initiator and target services are on separate computers.</span></span>  
  
```  
ssbdiagnose RUNTIME -ID D68D77A9-B1CF-41BF-A5CE-279ABCAB140D   
-TIMEOUT 10 CONNECT TO -E -S InitiatorComputer/InitiatorInstance   
-d InitiatorDatabase CONNECT TO -E -S TargetComputer/TargetInstance   
-d TargetDatabase  
```  
  
### <a name="h-monitor-the-status-of-a-conversation-in-two-databases-in-the-same-instance"></a><span data-ttu-id="f05ed-338">H.</span><span class="sxs-lookup"><span data-stu-id="f05ed-338">H.</span></span> <span data-ttu-id="f05ed-339">동일한 인스턴스의 두 데이터베이스에 있는 대화 상태 모니터링</span><span class="sxs-lookup"><span data-stu-id="f05ed-339">Monitor the status of a conversation in two databases in the same instance</span></span>  
 <span data-ttu-id="f05ed-340">다음 예에서는 시작자 서비스와 대상 서비스가 동일한 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스의 서로 다른 데이터베이스에 있는 특정 대화를 모니터링하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-340">The following example shows how to monitor a specific conversation where the initiator and target services are in separate databases in the same instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="f05ed-341">이 예에서는 **baseconnectionoptions** 를 사용하여 인스턴스 및 로그인 정보를 지정하고 두 개의 CONNECT TO 절을 사용하여 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-341">The example uses the **baseconnectionoptions** to specify the instance and login information, and two CONNECT TO clauses to specify the databases.</span></span> <span data-ttu-id="f05ed-342">-SHOWEVENTS는 모든 런타임 이벤트가 보고서 출력에 포함되도록 하기 위해 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-342">-SHOWEVENTS is specified so that all runtime events are included in the report output.</span></span>  
  
```  
ssbdiagnose -E -S TestComputer/DevTestInstance RUNTIME -SHOWEVENTS   
-ID 5094d4a7-e38c-4c37-da37-1d58b1cb8455 -TIMEOUT 10 CONNECT TO   
-d InitiatorDatabase CONNECT TO -d TargetDatabase  
```  
  
### <a name="i-monitor-the-status-of-two-conversations-between-two-databases"></a><span data-ttu-id="f05ed-343">9\.</span><span class="sxs-lookup"><span data-stu-id="f05ed-343">I.</span></span> <span data-ttu-id="f05ed-344">두 데이터베이스 간의 두 대화 상태 모니터링</span><span class="sxs-lookup"><span data-stu-id="f05ed-344">Monitor the status of two conversations between two databases</span></span>  
 <span data-ttu-id="f05ed-345">다음 예에서는 시작자 서비스와 대상 서비스가 동일한 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스의 서로 다른 데이터베이스에 있는 두 대화를 모니터링하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-345">The following example shows how to monitor two conversations where the initiator and target services are in separate databases in the same instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="f05ed-346">이 예에서는 **baseconnectionoptions** 를 사용하여 인스턴스 및 로그인 정보를 지정하고 두 개의 CONNECT TO 절을 사용하여 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-346">The example uses the **baseconnectionoptions** to specify the instance and login information, and two CONNECT TO clauses to specify the databases.</span></span>  
  
```  
ssbdiagnose -E -S TestComputer/DevTestInstance RUNTIME   
-ID 5094d4a7-e38c-4c37-da37-1d58b1cb8455   
-ID 9b293be9-226b-4e22-e169-1d2c2c15be86 -TIMEOUT 10 CONNECT TO   
-d InitiatorDatabase CONNECT TO -d TargetDatabase  
```  
  
### <a name="j-monitor-the-status-of-all-conversations-between-two-databases"></a><span data-ttu-id="f05ed-347">J.</span><span class="sxs-lookup"><span data-stu-id="f05ed-347">J.</span></span> <span data-ttu-id="f05ed-348">두 데이터베이스 간의 모든 대화 상태 모니터링</span><span class="sxs-lookup"><span data-stu-id="f05ed-348">Monitor the status of all conversations between two databases</span></span>  
 <span data-ttu-id="f05ed-349">다음 예에서는 동일한 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 있는 두 데이터베이스 간의 모든 대화를 모니터링하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-349">The following example shows how to monitor all the conversation between two databases in the same instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="f05ed-350">이 예에서는 **baseconnectionoptions** 를 사용하여 인스턴스 및 로그인 정보를 지정하고 두 개의 CONNECT TO 절을 사용하여 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-350">The example uses the **baseconnectionoptions** to specify the instance and login information, and two CONNECT TO clauses to specify the databases.</span></span>  
  
```  
ssbdiagnose -E -S TestComputer/DevTestInstance RUNTIME   
-TIMEOUT 10 CONNECT TO -d InitiatorDatabase CONNECT TO   
-d TargetDatabase  
```  
  
### <a name="k-ignore-specific-errors"></a><span data-ttu-id="f05ed-351">11.</span><span class="sxs-lookup"><span data-stu-id="f05ed-351">K.</span></span> <span data-ttu-id="f05ed-352">특정 오류 무시</span><span class="sxs-lookup"><span data-stu-id="f05ed-352">Ignore Specific Errors</span></span>  
 <span data-ttu-id="f05ed-353">다음 예에서는 현재 테스트 시스템의 활성화 구성 방식에서 알려진 오류(303 및 304)를 무시하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-353">The following example shows how to ignore known errors (303 and 304) in how activation is currently configured in a test system.</span></span>  
  
```  
ssbdiagnose -IGNORE 303 -IGNORE 304 -E -d TestDatabase   
CONFIGURATION FROM SERVICE /test/initiator TO SERVICE /test/target   
ON CONTRACT TextContract  
```  
  
### <a name="l-redirecting-ssbdiagnose-xml-output"></a><span data-ttu-id="f05ed-354">12.</span><span class="sxs-lookup"><span data-stu-id="f05ed-354">L.</span></span> <span data-ttu-id="f05ed-355">ssbdiagnose XML 출력 리디렉션</span><span class="sxs-lookup"><span data-stu-id="f05ed-355">Redirecting ssbdiagnose XML Output</span></span>  
 <span data-ttu-id="f05ed-356">다음 예에서는 **ssbdiagnose** 가 해당 출력을 파일로 리디렉션되는 XML 파일로 생성하도록 요청하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-356">The following example shows how to request that **ssbdiagnose** generate its output as an XML file that is redirected to a file.</span></span> <span data-ttu-id="f05ed-357">이 예에서 생성하는 TestDiag.xml 파일은 나중에 **ssbdiagnose** XML 파일을 분석하거나 보고하는 애플리케이션을 사용하여 열거나</span><span class="sxs-lookup"><span data-stu-id="f05ed-357">The TestDiag.xml file can then be opened by an application to analyze or report **ssbdiagnose** XML files.</span></span> <span data-ttu-id="f05ed-358">XML 메모장과 같은 일반적인 XML 편집기를 사용하여 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-358">Or, you can view it from a general XML editor such as XML Notepad.</span></span>  
  
```  
ssbdiagnose -XML -E -d MyDatabase CONFIGURATION FROM SERVICE   
/test/initiator TO SERVICE /test/target > c:\MyDiagnostics\TestDiag.xml  
```  
  
### <a name="m-using-an-environment-variable"></a><span data-ttu-id="f05ed-359">13.</span><span class="sxs-lookup"><span data-stu-id="f05ed-359">M.</span></span> <span data-ttu-id="f05ed-360">환경 변수 사용</span><span class="sxs-lookup"><span data-stu-id="f05ed-360">Using an Environment Variable</span></span>  
 <span data-ttu-id="f05ed-361">다음 예제에서는 먼저 서버 이름을 보유하는 SQLCMDSERVER 환경 변수를 설정한 후 **-S** 를 지정하지 않고 **ssbdiagnose**를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f05ed-361">The following example first sets the SQLCMDSERVER environment variable to hold the server name, and then runs **ssbdiagnose** without specifying **-S**.</span></span>  
  
```  
SET SQLCMDSERVER=MyComputer  
ssbdiagnose -XML -E -d MyDatabase CONFIGURATION FROM SERVICE   
/test/initiator TO SERVICE /test/target  
```  
  
## <a name="see-also"></a><span data-ttu-id="f05ed-362">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f05ed-362">See Also</span></span>  
 <span data-ttu-id="f05ed-363">[SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md) </span><span class="sxs-lookup"><span data-stu-id="f05ed-363">[SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md) </span></span>  
 <span data-ttu-id="f05ed-364">[BEGIN DIALOG CONVERSATION&#40;Transact-SQL&#41;](/sql/t-sql/statements/begin-dialog-conversation-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f05ed-364">[BEGIN DIALOG CONVERSATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/begin-dialog-conversation-transact-sql) </span></span>  
 <span data-ttu-id="f05ed-365">[CREATE BROKER PRIORITY&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-broker-priority-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f05ed-365">[CREATE BROKER PRIORITY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-broker-priority-transact-sql) </span></span>  
 <span data-ttu-id="f05ed-366">[CREATE CERTIFICATE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f05ed-366">[CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql) </span></span>  
 <span data-ttu-id="f05ed-367">[CREATE CONTRACT&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-contract-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f05ed-367">[CREATE CONTRACT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-contract-transact-sql) </span></span>  
 <span data-ttu-id="f05ed-368">[CREATE ENDPOINT&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f05ed-368">[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="f05ed-369">[CREATE MASTER KEY&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f05ed-369">[CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) </span></span>  
 <span data-ttu-id="f05ed-370">[CREATE MESSAGE TYPE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-message-type-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f05ed-370">[CREATE MESSAGE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-message-type-transact-sql) </span></span>  
 <span data-ttu-id="f05ed-371">[CREATE QUEUE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-queue-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f05ed-371">[CREATE QUEUE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-queue-transact-sql) </span></span>  
 <span data-ttu-id="f05ed-372">[CREATE REMOTE SERVICE BINDING&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-remote-service-binding-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f05ed-372">[CREATE REMOTE SERVICE BINDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-remote-service-binding-transact-sql) </span></span>  
 <span data-ttu-id="f05ed-373">[CREATE ROUTE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f05ed-373">[CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql) </span></span>  
 <span data-ttu-id="f05ed-374">[CREATE SERVICE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-service-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f05ed-374">[CREATE SERVICE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-service-transact-sql) </span></span>  
 <span data-ttu-id="f05ed-375">[RECEIVE &#40;Transact-SQL&#41;](/sql/t-sql/statements/receive-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f05ed-375">[RECEIVE &#40;Transact-SQL&#41;](/sql/t-sql/statements/receive-transact-sql) </span></span>  
 <span data-ttu-id="f05ed-376">[sys.transmission_queue&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-transmission-queue-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f05ed-376">[sys.transmission_queue &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-transmission-queue-transact-sql) </span></span>  
 <span data-ttu-id="f05ed-377">[sys.conversation_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-conversation-endpoints-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f05ed-377">[sys.conversation_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-conversation-endpoints-transact-sql) </span></span>  
 [<span data-ttu-id="f05ed-378">sys.conversation_groups&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f05ed-378">sys.conversation_groups &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-conversation-groups-transact-sql)  
  
  

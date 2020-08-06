---
title: 로그 속성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- QueryLogFileSize property
- QueryLogTableName property
- TraceBackgroundDistributionPeriod property
- TraceMaxRowsetSize property
- NullKeyConvertedToUnknown property
- CrashReportsFolder property
- TraceDefinitionFile property
- SQLDumperFlagsOn property
- KeyErrorLimit property
- SnapshotDefinitionFile property
- MinidumpErrorList property
- ErrorLogFileName property
- KeyDuplicate property
- IgnoreDataTruncation property
- logs [Analysis Services]
- Enabled property
- FileSizeMB property
- TraceFileWriteTrailerPeriod property
- TraceQueryResponseTextChunkSize property
- File property
- FileBufferSize property
- TraceRowsetBackgroundFlushPeriod property
- ErrorLogFileSize property
- TraceRequestParameters property
- KeyErrorLimitAction property
- CreateQueryLogTable property
- LogDir property
- TraceBackgroundFlushPeriod property
- TraceFileBufferSize property
- SQLDumperFlagsOff property
- QueryLogConnectionString property
- KeyNotFound property
- KeyErrorLogFile property
- TraceReportFQDN property
- KeyErrorAction property
- QueryLogFileName property
- MessageLogs property
- MiniDumpFlagsOn property
- SnapshotFrequencySec property
- QueryLogSampling property
- CreateAndSendCrashReports property
- LogDurationSec property
ms.assetid: 33fd90ee-cead-48f0-8ff9-9b458994c766
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3761ce3dca232db8968a2a7cba083dcc5554d792
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743487"
---
# <a name="log-properties"></a><span data-ttu-id="0a517-102">로그 속성</span><span class="sxs-lookup"><span data-stu-id="0a517-102">Log Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="0a517-103">에서는 다음 표에 나열된 로그 서버 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-103">supports the log server properties listed in the following tables.</span></span> <span data-ttu-id="0a517-104">추가 서버 속성 및 해당 속성 설정 방법은 [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0a517-104">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
## <a name="general"></a><span data-ttu-id="0a517-105">일반</span><span class="sxs-lookup"><span data-stu-id="0a517-105">General</span></span>  
 `File`  
 <span data-ttu-id="0a517-106">서버 로그 파일의 이름을 식별하는 문자열 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-106">A string property that identifies the name of the server log file.</span></span> <span data-ttu-id="0a517-107">이 속성은 데이터베이스 테이블과는 달리 디스크 파일이 로깅용으로 사용되는 경우에만 적용됩니다(기본 동작).</span><span class="sxs-lookup"><span data-stu-id="0a517-107">This property only applies when a disk file is used for logging, as opposed to a database table (the default behavior).</span></span>  
  
 <span data-ttu-id="0a517-108">이 속성의 기본값은 msmdsrv.log입니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-108">The default value for this property is msmdsrv.log.</span></span>  
  
 `FileBufferSize`  
 <span data-ttu-id="0a517-109">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-109">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MessageLogs`  
 <span data-ttu-id="0a517-110">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-110">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="error-log"></a><span data-ttu-id="0a517-111">오류 로그</span><span class="sxs-lookup"><span data-stu-id="0a517-111">Error Log</span></span>  
 <span data-ttu-id="0a517-112">서버 인스턴스 수준에서 이러한 속성을 설정하여 다른 도구 및 디자이너에 나타나는 오류 구성에 대한 기본값을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-112">You can set these properties at the server instance level to modify the default values for Error Configuration that appear in other tools and designers.</span></span> <span data-ttu-id="0a517-113">자세한 내용은 [&#41;&#40;큐브, 파티션 및 차원 처리에 대 한 오류 구성](../multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md) 을 참조 하세요 <xref:Microsoft.AnalysisServices.MiningStructure.ErrorConfiguration%2A> .</span><span class="sxs-lookup"><span data-stu-id="0a517-113">See [Error Configuration for Cube, Partition, and Dimension Processing &#40;SSAS - Multidimensional&#41;](../multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md) and <xref:Microsoft.AnalysisServices.MiningStructure.ErrorConfiguration%2A> for more information.</span></span>  
  
 <span data-ttu-id="0a517-114">**ErrorLog\ErrorLogFileName**</span><span class="sxs-lookup"><span data-stu-id="0a517-114">**ErrorLog\ErrorLogFileName**</span></span>  
 <span data-ttu-id="0a517-115">서버가 수행한 작업을 처리하는 동안 속성이 기본값으로 사용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-115">A property used as a default during processing operation performed by the server.</span></span>  
  
 <span data-ttu-id="0a517-116">**ErrorLog\ErrorLogFileSize**</span><span class="sxs-lookup"><span data-stu-id="0a517-116">**ErrorLog\ErrorLogFileSize**</span></span>  
 <span data-ttu-id="0a517-117">서버가 수행한 작업을 처리하는 동안 속성이 기본값으로 사용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-117">A property used as a default during processing operation performed by the server.</span></span>  
  
 <span data-ttu-id="0a517-118">**ErrorLog\KeyErrorAction**</span><span class="sxs-lookup"><span data-stu-id="0a517-118">**ErrorLog\KeyErrorAction**</span></span>  
 <span data-ttu-id="0a517-119">`KeyNotFound` 오류가 발생할 때 서버에서 수행하는 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-119">Specifies the action taken by the server when a `KeyNotFound` error occurs.</span></span> <span data-ttu-id="0a517-120">이 오류에 대한 유효한 응답은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-120">Valid responses to this error include:</span></span>  
  
-   <span data-ttu-id="0a517-121">`ConvertToUnknown`은 오류 키 값을 알 수 없는 멤버에 할당하도록 서버에 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-121">`ConvertToUnknown` tells the server to allocate the error key value to the unknown member.</span></span>  
  
-   <span data-ttu-id="0a517-122">`DiscardRecord`는 레코드를 제외하도록 서버에 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-122">`DiscardRecord` tells the server to exclude the record.</span></span>  
  
 <span data-ttu-id="0a517-123">**ErrorLog\KeyErrorLogFile**</span><span class="sxs-lookup"><span data-stu-id="0a517-123">**ErrorLog\KeyErrorLogFile**</span></span>  
 <span data-ttu-id="0a517-124">서비스 계정이 읽기-쓰기 권한을 가지고 있는 폴더에 있는 사용자 정의 파일 이름이며, 이 파일의 확장명은 .log여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-124">This is a user-defined filename that must have a .log file extension, located in a folder on which the service account has read-write permissions.</span></span> <span data-ttu-id="0a517-125">이 로그 파일에는 처리 중에 생성된 오류만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-125">This log file will only contain errors generated during processing.</span></span> <span data-ttu-id="0a517-126">보다 자세한 정보가 필요한 경우 비행 레코더를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="0a517-126">Use the Flight Recorder if you require more detailed information.</span></span>  
  
 <span data-ttu-id="0a517-127">**ErrorLog\KeyErrorLimit**</span><span class="sxs-lookup"><span data-stu-id="0a517-127">**ErrorLog\KeyErrorLimit**</span></span>  
 <span data-ttu-id="0a517-128">서버에서 처리를 중지하기 전에 허용할 데이터 무결성 오류의 최대 수입니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-128">This is the maximum number of data integrity errors that the server will allow before failing the processing.</span></span> <span data-ttu-id="0a517-129">-1 값은 제한이 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-129">A value of -1 indicates that there is no limit.</span></span> <span data-ttu-id="0a517-130">기본값은 0이며 처음 오류가 발생한 후 처리가 중지됨을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-130">The default is 0, which means processing stops after the first error occurs.</span></span> <span data-ttu-id="0a517-131">이 값을 정수로 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-131">You can also set it to a whole number.</span></span>  
  
 <span data-ttu-id="0a517-132">**ErrorLog\KeyErrorLimitAction**</span><span class="sxs-lookup"><span data-stu-id="0a517-132">**ErrorLog\KeyErrorLimitAction**</span></span>  
 <span data-ttu-id="0a517-133">키 오류 수가 상한에 도달한 경우 서버에서 수행하는 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-133">Specifies the action taken by the server when the number of key errors has reached the upper limit.</span></span> <span data-ttu-id="0a517-134">이 동작에 대한 유효한 응답은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-134">Valid responses to this action include:</span></span>  
  
-   <span data-ttu-id="0a517-135">`StopProcessing`은 오류 제한에 도달하는 경우 처리를 중지하도록 서버에 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-135">`StopProcessing` tells the server to stop processing when the error limit is reached.</span></span>  
  
-   <span data-ttu-id="0a517-136">`StopLogging`은 오류 제한에 도달하는 경우 오류 기록을 중지하되 처리를 계속하도록 서버에 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-136">`StopLogging` tells the server to stop logging errors when the error limit is reached, but allow processing to continue.</span></span>  
  
 <span data-ttu-id="0a517-137">**ErrorLog\ LogErrorTypes\KeyNotFound**</span><span class="sxs-lookup"><span data-stu-id="0a517-137">**ErrorLog\ LogErrorTypes\KeyNotFound**</span></span>  
 <span data-ttu-id="0a517-138">`KeyNotFound` 오류가 발생할 때 서버에서 수행하는 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-138">Specifies the action taken by the server when a `KeyNotFound` error occurs.</span></span> <span data-ttu-id="0a517-139">이 오류에 대한 유효한 응답은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-139">Valid responses to this error include:</span></span>  
  
-   <span data-ttu-id="0a517-140">`IgnoreError`는 오류를 기록하거나 키 오류 제한에 대해 오류 개수를 계산하지 않고 처리를 계속하도록 서버에 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-140">`IgnoreError` tells the server to continue processing without logging the error or counting it towards the key error limit.</span></span> <span data-ttu-id="0a517-141">오류를 무시하기만 하면 오류 개수에 추가하거나 화면 또는 로그 파일에 기록하지 않고 처리가 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-141">By ignoring the error, you simply allow processing to continue without adding to the error count or logging it to the screen or log file.</span></span> <span data-ttu-id="0a517-142">문제의 레코드에 데이터 무결성 문제가 있어서 데이터베이스에 레코드를 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-142">The record in question has a data integrity problem and cannot be added to the database.</span></span> <span data-ttu-id="0a517-143">레코드는 `KeyErrorAction` 속성으로 결정된 대로 삭제되거나 알 수 없는 멤버에 집계됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-143">The record will either be discarded or aggregated to Unknown Member, as determined by the `KeyErrorAction` property.</span></span>  
  
-   <span data-ttu-id="0a517-144">`ReportAndContinue`는 오류를 기록하고 키 오류 제한에 오류 수를 계산하고 처리를 계속하도록 서버에 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-144">`ReportAndContinue` tells the server to log the error, count it towards the key error limit, and continue processing.</span></span> <span data-ttu-id="0a517-145">오류를 발생시키는 레코드는 삭제되거나 알 수 없는 멤버로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-145">The record triggering the error is discarded or converted to Unknown Member.</span></span>  
  
-   <span data-ttu-id="0a517-146">`ReportAndStop`은 키 오류 제한에 관계없이 오류를 기록하고 즉시 처리를 중지하도록 서버에 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-146">`ReportAndStop` tells the server to log the error and stop processing immediately, regardless of the key error limit.</span></span> <span data-ttu-id="0a517-147">오류를 발생시키는 레코드는 삭제되거나 알 수 없는 멤버로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-147">The record triggering the error is discarded or converted to Unknown Member.</span></span>  
  
 <span data-ttu-id="0a517-148">**ErrorLog\ LogErrorTypes\KeyDuplicate**</span><span class="sxs-lookup"><span data-stu-id="0a517-148">**ErrorLog\ LogErrorTypes\KeyDuplicate**</span></span>  
 <span data-ttu-id="0a517-149">중복 키가 있을 때 서버가 수행하는 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-149">Specifies the action taken by the server when a duplicate key is found.</span></span> <span data-ttu-id="0a517-150">유효한 값에는 오류가 발생하지 않은 것처럼 처리를 계속하는 `IgnoreError`, 오류를 기록하고 처리를 계속하는 `ReportAndContinue`, 오류를 기록하고 오류 개수가 오류 제한에 못 미치더라도 처리를 즉시 중지하는 `ReportAndStop`이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-150">Valid values include `IgnoreError` to continue processing as if the error did not occur, `ReportAndContinue` to log the error and continue processing, and `ReportAndStop` to log the error and stop processing immediately, even if the error count is below the error limit.</span></span>  
  
 <span data-ttu-id="0a517-151">**ErrorLog\ LogErrorTypes\NullKeyConvertedToUnknown**</span><span class="sxs-lookup"><span data-stu-id="0a517-151">**ErrorLog\ LogErrorTypes\NullKeyConvertedToUnknown**</span></span>  
 <span data-ttu-id="0a517-152">null 키가 알 수 없는 멤버로 변환된 경우 서버에서 수행하는 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-152">Specifies the action taken by the server when a null key has been converted to Unknown Member.</span></span> <span data-ttu-id="0a517-153">유효한 값에는 오류가 발생하지 않은 것처럼 처리를 계속하는 `IgnoreError`, 오류를 기록하고 처리를 계속하는 `ReportAndContinue`, 오류를 기록하고 오류 개수가 오류 제한에 못 미치더라도 처리를 즉시 중지하는 `ReportAndStop`이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-153">Valid values include `IgnoreError` to continue processing as if the error did not occur, `ReportAndContinue` to log the error and continue processing, and `ReportAndStop` to log the error and stop processing immediately, even if the error count is below the error limit.</span></span>  
  
 <span data-ttu-id="0a517-154">**ErrorLog\ LogErrorTypes\NullKeyNotAllowed**</span><span class="sxs-lookup"><span data-stu-id="0a517-154">**ErrorLog\ LogErrorTypes\NullKeyNotAllowed**</span></span>  
 <span data-ttu-id="0a517-155">차원 특성에 대해 `NullProcessing`이 `Error`로 설정된 경우 서버에서 수행하는 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-155">Specifies the action taken by the server when `NullProcessing` is set to `Error` for a dimension attribute.</span></span> <span data-ttu-id="0a517-156">null 값이 지정된 특성에서 허용되지 않는 경우 오류가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-156">An error is generated when a null value is not allowed in a given attribute.</span></span> <span data-ttu-id="0a517-157">이 오류 구성 속성은 오류를 보고하고 오류 제한에 도달할 때까지 처리를 계속하는 다음 단계를 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-157">This error configuration property informs the next step, which is to report the error and continue processing until the error limit is reached.</span></span> <span data-ttu-id="0a517-158">유효한 값에는 오류가 발생하지 않은 것처럼 처리를 계속하는 `IgnoreError`, 오류를 기록하고 처리를 계속하는 `ReportAndContinue`, 오류를 기록하고 오류 개수가 오류 제한에 못 미치더라도 처리를 즉시 중지하는 `ReportAndStop`이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-158">Valid values include `IgnoreError` to continue processing as if the error did not occur, `ReportAndContinue` to log the error and continue processing, and `ReportAndStop` to log the error and stop processing immediately, even if the error count is below the error limit.</span></span>  
  
 <span data-ttu-id="0a517-159">**ErrorLog\ LogErrorTypes\CalculationError**</span><span class="sxs-lookup"><span data-stu-id="0a517-159">**ErrorLog\ LogErrorTypes\CalculationError**</span></span>  
 <span data-ttu-id="0a517-160">서버가 수행한 작업을 처리하는 동안 속성이 기본값으로 사용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-160">A property used as a default during processing operation performed by the server.</span></span>  
  
 <span data-ttu-id="0a517-161">**ErrorLog\IgnoreDataTruncation**</span><span class="sxs-lookup"><span data-stu-id="0a517-161">**ErrorLog\IgnoreDataTruncation**</span></span>  
 <span data-ttu-id="0a517-162">서버가 수행한 작업을 처리하는 동안 속성이 기본값으로 사용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-162">A property used as a default during processing operation performed by the server.</span></span>  
  
## <a name="exception"></a><span data-ttu-id="0a517-163">예외</span><span class="sxs-lookup"><span data-stu-id="0a517-163">Exception</span></span>  
 <span data-ttu-id="0a517-164">**Exception\CreateAndSendCrashReports**</span><span class="sxs-lookup"><span data-stu-id="0a517-164">**Exception\CreateAndSendCrashReports**</span></span>  
 <span data-ttu-id="0a517-165">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-165">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0a517-166">**Exception\CrashReportsFolder**</span><span class="sxs-lookup"><span data-stu-id="0a517-166">**Exception\CrashReportsFolder**</span></span>  
 <span data-ttu-id="0a517-167">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-167">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0a517-168">**Exception\SQLDumperFlagsOn**</span><span class="sxs-lookup"><span data-stu-id="0a517-168">**Exception\SQLDumperFlagsOn**</span></span>  
 <span data-ttu-id="0a517-169">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-169">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0a517-170">**Exception\SQLDumperFlagsOff**</span><span class="sxs-lookup"><span data-stu-id="0a517-170">**Exception\SQLDumperFlagsOff**</span></span>  
 <span data-ttu-id="0a517-171">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-171">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0a517-172">**Exception\MiniDumpFlagsOn**</span><span class="sxs-lookup"><span data-stu-id="0a517-172">**Exception\MiniDumpFlagsOn**</span></span>  
 <span data-ttu-id="0a517-173">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-173">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0a517-174">**Exception\MinidumpErrorList**</span><span class="sxs-lookup"><span data-stu-id="0a517-174">**Exception\MinidumpErrorList**</span></span>  
 <span data-ttu-id="0a517-175">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-175">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="flight-recorder"></a><span data-ttu-id="0a517-176">비행 레코더</span><span class="sxs-lookup"><span data-stu-id="0a517-176">Flight Recorder</span></span>  
 <span data-ttu-id="0a517-177">**FlightRecorder\Enabled**</span><span class="sxs-lookup"><span data-stu-id="0a517-177">**FlightRecorder\Enabled**</span></span>  
 <span data-ttu-id="0a517-178">비행 레코더 기능이 설정되어 있는지 여부를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-178">A Boolean property that indicates whether the flight recorder feature is enabled.</span></span>  
  
 <span data-ttu-id="0a517-179">**FlightRecorder\FileSizeMB**</span><span class="sxs-lookup"><span data-stu-id="0a517-179">**FlightRecorder\FileSizeMB**</span></span>  
 <span data-ttu-id="0a517-180">비행 레코더 디스크 파일의 크기(MB)를 정의하는 부호 있는 32비트 정수 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-180">A signed 32-bit integer property that defines the size of the flight recorder disk file, in megabytes.</span></span>  
  
 <span data-ttu-id="0a517-181">**FlightRecorder\LogDurationSec**</span><span class="sxs-lookup"><span data-stu-id="0a517-181">**FlightRecorder\LogDurationSec**</span></span>  
 <span data-ttu-id="0a517-182">비행 레코더가 롤오버된 빈도(초)를 정의하는 부호 있는 32비트 정수 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-182">A signed 32-bit integer property that defines the frequency that the flight recorder is rolled over, in seconds.</span></span>  
  
 <span data-ttu-id="0a517-183">**FlightRecorder\SnapshotDefinitionFile**</span><span class="sxs-lookup"><span data-stu-id="0a517-183">**FlightRecorder\SnapshotDefinitionFile**</span></span>  
 <span data-ttu-id="0a517-184">스냅샷을 사용할 때 서버에 실행된 검색 명령을 포함하여 스냅샷 정의 파일의 이름을 정의하는 문자열 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-184">A string property that defines the name of the snapshot definition file, containing discover commands that are issued to the server when a snapshot is taken.</span></span>  
  
 <span data-ttu-id="0a517-185">이 속성의 기본값은 빈 문자열이며 이후 파일 이름 FlightRecorderSnapshotDef.xml이 기본값이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-185">The default value for this property is blank, which in turn defaults to file name FlightRecorderSnapshotDef.xml.</span></span>  
  
 <span data-ttu-id="0a517-186">**FlightRecorder\SnapshotFrequencySec**</span><span class="sxs-lookup"><span data-stu-id="0a517-186">**FlightRecorder\SnapshotFrequencySec**</span></span>  
 <span data-ttu-id="0a517-187">스냅샷 빈도(초)를 정의하는 부호 있는 32비트 정수 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-187">A signed 32-bit integer property that defines the snapshot frequency, in seconds.</span></span>  
  
 <span data-ttu-id="0a517-188">**FlightRecorder\TraceDefinitionFile**</span><span class="sxs-lookup"><span data-stu-id="0a517-188">**FlightRecorder\TraceDefinitionFile**</span></span>  
 <span data-ttu-id="0a517-189">비행 레코더 추적 정의 파일의 이름을 지정하는 문자열 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-189">A string property that specifies the name of the flight recorder trace definition file.</span></span>  
  
 <span data-ttu-id="0a517-190">이 속성의 기본값은 빈 문자열이며 이후 FlightRecorderTraceDef.xml이 기본값이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-190">The default value for this property is blank, which in turn defaults to FlightRecorderTraceDef.xml.</span></span>  
  
## <a name="query-log"></a><span data-ttu-id="0a517-191">쿼리 로그</span><span class="sxs-lookup"><span data-stu-id="0a517-191">Query Log</span></span>  
 <span data-ttu-id="0a517-192">**적용 대상:** 다차원 서버 모드에만 해당</span><span class="sxs-lookup"><span data-stu-id="0a517-192">**Applies to:** Multidimensional server mode only</span></span>  
  
 <span data-ttu-id="0a517-193">**QueryLog\QueryLogFileName**</span><span class="sxs-lookup"><span data-stu-id="0a517-193">**QueryLog\QueryLogFileName**</span></span>  
 <span data-ttu-id="0a517-194">쿼리 로그 파일의 이름을 지정하는 문자열 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-194">A string property that specifies the name of the query log file.</span></span> <span data-ttu-id="0a517-195">이 속성은 데이터베이스 테이블과는 달리 디스크 파일이 로깅용으로 사용되는 경우에만 적용됩니다(기본 동작).</span><span class="sxs-lookup"><span data-stu-id="0a517-195">This property only applies when a disk file is used for logging, as opposed to a database table (the default behavior).</span></span>  
  
 <span data-ttu-id="0a517-196">**QueryLog\QueryLogSampling**</span><span class="sxs-lookup"><span data-stu-id="0a517-196">**QueryLog\QueryLogSampling**</span></span>  
 <span data-ttu-id="0a517-197">쿼리 로그 샘플링 비율을 지정하는 부호 있는 32비트 정수 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-197">A signed 32-bit integer property that specifies the query log sampling rate.</span></span>  
  
 <span data-ttu-id="0a517-198">이 속성의 기본값은 10으로 서버 쿼리 10개마다 1개가 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-198">The default value for this property is 10, meaning that 1 out of every 10 server queries is logged.</span></span>  
  
 <span data-ttu-id="0a517-199">**QueryLog\QueryLogFileSize**</span><span class="sxs-lookup"><span data-stu-id="0a517-199">**QueryLog\QueryLogFileSize**</span></span>  
 <span data-ttu-id="0a517-200">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-200">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0a517-201">**QueryLog\QueryLogConnectionString**</span><span class="sxs-lookup"><span data-stu-id="0a517-201">**QueryLog\QueryLogConnectionString**</span></span>  
 <span data-ttu-id="0a517-202">쿼리 로그 데이터베이스에 대한 연결을 지정하는 문자열 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-202">A string property that specifies the connection to the query log database.</span></span>  
  
 <span data-ttu-id="0a517-203">**QueryLog\QueryLogTableName**</span><span class="sxs-lookup"><span data-stu-id="0a517-203">**QueryLog\QueryLogTableName**</span></span>  
 <span data-ttu-id="0a517-204">쿼리 로그 테이블의 이름을 지정하는 문자열 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-204">A string property that specifies the name of the query log table.</span></span>  
  
 <span data-ttu-id="0a517-205">이 속성의 기본값은 OlapQueryLog입니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-205">The default value for this property is OlapQueryLog.</span></span>  
  
 <span data-ttu-id="0a517-206">**QueryLog\CreateQueryLogTable**</span><span class="sxs-lookup"><span data-stu-id="0a517-206">**QueryLog\CreateQueryLogTable**</span></span>  
 <span data-ttu-id="0a517-207">쿼리 로그 테이블을 만들지 여부를 지정하는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-207">A Boolean property that specifies whether to create the query log table.</span></span>  
  
 <span data-ttu-id="0a517-208">이 속성의 기본값은 False로 서버가 로그 테이블을 자동으로 만들지 않고 쿼리 이벤트를 기록하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-208">The default value for this property is false, which indicates the server will not automatically create the log table and will not log query events.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0a517-209">쿼리 로그를 구성 하는 방법에 대 한 자세한 내용은 [Analysis Services의 로그 작업](../instances/log-operations-in-analysis-services.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0a517-209">For more information about configuring the query log, see [Log operations in Analysis Services](../instances/log-operations-in-analysis-services.md).</span></span>  
  
## <a name="trace"></a><span data-ttu-id="0a517-210">Trace</span><span class="sxs-lookup"><span data-stu-id="0a517-210">Trace</span></span>  
 <span data-ttu-id="0a517-211">**Trace\TraceBackgroundDistributionPeriod**</span><span class="sxs-lookup"><span data-stu-id="0a517-211">**Trace\TraceBackgroundDistributionPeriod**</span></span>  
 <span data-ttu-id="0a517-212">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-212">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0a517-213">**Trace\TraceBackgroundFlushPeriod**</span><span class="sxs-lookup"><span data-stu-id="0a517-213">**Trace\TraceBackgroundFlushPeriod**</span></span>  
 <span data-ttu-id="0a517-214">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-214">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0a517-215">**Trace\TraceFileBufferSize**</span><span class="sxs-lookup"><span data-stu-id="0a517-215">**Trace\TraceFileBufferSize**</span></span>  
 <span data-ttu-id="0a517-216">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-216">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0a517-217">**Trace\TraceFileWriteTrailerPeriod**</span><span class="sxs-lookup"><span data-stu-id="0a517-217">**Trace\TraceFileWriteTrailerPeriod**</span></span>  
 <span data-ttu-id="0a517-218">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-218">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0a517-219">**Trace\TraceMaxRowsetSize**</span><span class="sxs-lookup"><span data-stu-id="0a517-219">**Trace\TraceMaxRowsetSize**</span></span>  
 <span data-ttu-id="0a517-220">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-220">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0a517-221">**Trace\TraceProtocolTraffic**</span><span class="sxs-lookup"><span data-stu-id="0a517-221">**Trace\TraceProtocolTraffic**</span></span>  
 <span data-ttu-id="0a517-222">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-222">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0a517-223">**Trace\TraceQueryResponseTextChunkSize**</span><span class="sxs-lookup"><span data-stu-id="0a517-223">**Trace\TraceQueryResponseTextChunkSize**</span></span>  
 <span data-ttu-id="0a517-224">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-224">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0a517-225">**Trace\TraceReportFQDN**</span><span class="sxs-lookup"><span data-stu-id="0a517-225">**Trace\TraceReportFQDN**</span></span>  
 <span data-ttu-id="0a517-226">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-226">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0a517-227">**Trace\TraceRequestParameters**</span><span class="sxs-lookup"><span data-stu-id="0a517-227">**Trace\TraceRequestParameters**</span></span>  
 <span data-ttu-id="0a517-228">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-228">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="0a517-229">**Trace\TraceRowsetBackgroundFlushPeriod**</span><span class="sxs-lookup"><span data-stu-id="0a517-229">**Trace\TraceRowsetBackgroundFlushPeriod**</span></span>  
 <span data-ttu-id="0a517-230">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a517-230">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a517-231">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0a517-231">See Also</span></span>  
 <span data-ttu-id="0a517-232">[Analysis Services에서 서버 속성 구성](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="0a517-232">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="0a517-233">Analysis Services 인스턴스의 서버 모드 확인</span><span class="sxs-lookup"><span data-stu-id="0a517-233">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  

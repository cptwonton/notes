ultimately not needed but was used in AMS batch job


    @Bean
    @JobScope
    public Step deleteCounts() {
        return stepBuilderFactory.get("deleteCounts")
                .tasklet((stepContribution, chunkContext) -> {
                    CountDataMapper countDataMapper = sqlSession.getMapper(CountDataMapper.class);
                    countDataMapper.delete();
                    return RepeatStatus.FINISHED;
                }).build();
    }
